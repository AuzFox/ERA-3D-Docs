# Memory Map

## Introduction

This page details ERA-3D's memory map, as of version `0.0.0`.

Many things in ERA-3D are mapped into virtual memory, and can be modified using pointers to certain addresses.

The following table lists all memory regions in the memory map, and each region is explained below.

!!! info
	All memory in ERA-3D is arranged in [big-endian](https://en.wikipedia.org/wiki/Endianness) format.

## Memory Regions Table

Memory Region     | Size             | Address Range           | Description
------------------|------------------|-------------------------|------------
__System Memory__ |                  |                         |
`HEAP`            | `8MiB`           | `0x00000000-0x007FFFFF` | General purpose RAM
`TEXMEM`          | `4MiB`           | `0x00800000-0x00BFFFFF` | Texture data
`OBJMEM`          | `3MiB + 384KiB`  | `0x00C00000-0x00F5FFFF` | Mesh data
`AOBMEM`          | `8KiB`           | `0x00F60000-0x00F61FFF` | Audio output buffer
`SYSMEM`          | `632KiB`         | `0x00F62000-0x00FFFFFF` | System state memory
`WAVMEM`          | `7MiB`           | `0x01000000-0x016FFFFF` | Audio wave data
`SEQMEM`          | `256KiB`         | `0x01700000-0x0173FFFF` | Audio sequencer data
`GLOBALS`         | `256KiB`         | `0x01740000-0x0177FFFF` | VM global variables
`LOCALS`          | `256KiB`         | `0x01780000-0x017BFFFF` | VM local variables
`ARGS`            | `256KiB`         | `0x017C0000-0x017FFFFF` | VM function arguments
__Cartridge ROM__ |                  |                         |
`TEXBANK[0-3]`    | `16MiB`          | `0x01800000-0x027FFFFF` | 4 texture banks
`OBJBANK[0-3]`    | `13MiB + 512KiB` | `0x02800000-0x0357FFFF` | 4 mesh data banks
`OMPBANK[0-3]`    | `1MiB + 256KiB`  | `0x03580000-0x036BFFFF` | 4 object maps for `OBJBANK[0-3]`
`WMPBANK[0-1]`    | `1MiB + 256KiB`  | `0x036C0000-0x037FFFFF` | 2 wave maps for `WAVBANK[0-1]`
`WAVBANK[0-1]`    | `14MiB`          | `0x03800000-0x045FFFFF` | 2 wave data banks
`SEQBANK[0-7]`    | `2MiB`           | `0x04600000-0x047FFFFF` | 8 audio sequencer data banks
`ROM`             | `16MiB`          | `0x04800000-0x057FFFFF` | String data + user ROM
__Memory Card__   |                  |                         |
`MEMCARD`         | `4KiB`           | `0x05800000-0x05800FFF` | Persistent save data

## System Memory

System memory is the region of memory that contains all data mapped to the system's internal RAM.

Data in this memory region can be read from and written to.

### `HEAP`

Address range: `0x00000000-0x007FFFFF`

Accessible using constant `MEMORY_HEAP`. (Or using an address of 0.)

The heap is an 8MiB block of general-purpose RAM that can be used in any way the user sees fit.

The [`alloc()`](api-reference.md/#alloc), [`realloc()`](api-reference.md/#realloc), and [`free()`](api-reference.md/#free) API functions can be used to allocate and deallocate memory blocks in the heap for dynamic memory management.

Alternatively, the user may choose to manage the heap manually.

### `TEXMEM`

Address range: `0x00800000-0x00BFFFFF`

Accessible using constant `MEMORY_TEXMEM`.

Contains the currently loaded texture data.

`TEXMEM` can be treated as a 1024x1024 2D array of 32-bit RGBA pixel values.

!!! warning
	Updates to `TEXMEM` should only be done during `init()` and `update()`.

```C
// get a pointer to the start of TEXMEM
int* texture_data = MEMORY_TEXMEM;

// fetch the pixel value at (x=32, y=64)
int x = 32;
int y = 64;
int pixel_value = texture_data[y * 1024 + x];

// set the pixel at (x=32, y=64) to white
texture_data[y * 1024 + x] = 0xFFFFFFFF;
```

### `OBJMEM`

Address range: `0x00C00000-0x00F5FFFF`

Accessible using constant `MEMORY_OBJMEM`.

Contains the currently loaded mesh data.

There is enough space for 32768 triangles (or 98304 vertices) to be loaded at once.

!!! info
	Mesh data stored in this region should not be confused with vertices submitted directly using the `mesh*()` API functions.

	Vertices submitted using `mesh*()` functions are not accessible in the memory map.

	`OBJMEM` is intended to store relatively static meshes, though it is still possible to modify `OBJMEM` meshes at runtime.

`OBJMEM` can be treated as an array of `vertex` structs.

```C
// get a pointer to the start of OBJMEM
vertex* obj_data = MEMORY_OBJMEM;

// fetch the first loaded vertex
vertex vert = obj_data[0];

// update the first vertex in OBJMEM
obj_data[0] = vertex(
	vec3(1.0, 2.0, 3.0), // position
	vec3Up(),            // normal
	vec2(),              // uv
	0xFF00FFFF           // color
);
```

Meshes stored in `OBJMEM` can be drawn using the `drawObj()` and `drawObjEx()` API functions.

`drawObj()` uses the [Object Map (`OBJMAP`)](#objmap) to draw a predefined mesh. (The `OBJMAP` is detailed in the `SYSMEM` section.)

```C
void draw() {

	// ...

	pushMatrix();
		// ... translate(), rotate(), and scale() as desired ...
		
		// draw the mesh defined by OBJMAP entry 0
		drawObj(0);
	popMatrix();
}
```

`drawObjEx()` accepts parameters to control which vertices from `OBJMEM` are drawn.

```C
void draw() {

	// ...

	pushMatrix();
		// ... translate(), rotate(), and scale() as desired ...
		
		// draw the first triangle in OBJMEM
		drawObjEx(
			MESH_TRIANGLES, // mesh primitive type: MESH_LINES, MESH_TRIANGLES, or MESH_QUADS
			0, // start vertex index
			1  // number of primitives to draw
		);
	popMatrix();
}
```

### `AOBMEM`

Address range: `0x00F60000-0x00F61FFF`

Accessible using constant `MEMORY_AOBMEM`.

Contains the system audio output data.

Audio samples stored in `AOBMEM` are 16-bit signed integer values that come in pairs for stereo audio.

Samples are arranged such that:

- The first 16-bit value is the first sample for the left speaker
- The second value is the first sample for the right speaker
- The third value is the second sample for the left speaker

and so on.

`AOBMEM` contains 2048 sample pairs, which are played at a sample rate of 22050hz.

!!! warning
	Any changes made to audio output samples will currently be overwritten by the soundchip.

	Facilities for control over audio output are planned for the future.

### `SYSMEM`

Address range: `0x00F62000-0x00FFFFFF`

Accessible using constant `MEMORY_SYSMEM`.

Contains state data for many aspects of the system.

`SYSMEM` is divided into multiple sub-regions, which are detailed below.

#### Soundchip State

Address range: `0x00F62000-0x00F62053`

Contains the state of the soundchip.

The soundchip state is layed out as follows:

Address(es) | Size | Description
-|-|-
`0x00F62000` | 1 byte | Track enabled flags; the most significant bit enables track 0
`0x00F62001-0x00F62050` | 80 bytes | Track states; 10 bytes per track, 8 tracks
`0x00F62051-0x00F62053` | 3 bytes | Unused

Track states are 10 bytes each, and have the following layout:

Byte Index | Description
-|-
0 | Playback Flags
1 | BPM
2 | Volume
3 | Panning
4 | (Reserved for future use)
5 | Song Position
6 | Pattern ID
7 | Pattern Position
8 | Groove ID
9 | Groove Position

#### `OBJMAP`

Address range: `0x00F62054-0x00F63853`

Accessible using constant `MEMORY_OBJMAP`.

Contains a table of 512 user-defined mesh objects.

Each entry in the `OBJMAP` consists of 3 32-bit `int` values, detailed in the following table:

`int` Index | Description
-|-
0 | Primitive type (must be `MESH_LINES`, `MESH_TRIANGLES`, or `MESH_QUADS`)
1 | Start `OBJMEM` vertex index
2 | Primitive count

The `drawObj()` API function accepts an index and will draw the mesh described by the corresponding entry in the `OBJMAP` table.

```C
void init() {
	// configure a custom OBJMAP entry
	
	// get a pointer to the first OBJMAP entry (entry index 0)
	int* objmap_ptr = MEMORY_OBJMAP;

	// set OBJMAP entry values
	objmap_ptr[0] = MESH_TRIANGLES; // primitive type
	objmap_ptr[1] = 0; // start OBJMEM vertex index
	objmap_ptr[2] = 1; // primitive count
}

void draw() {

	// ...

	pushMatrix();
		// ... translate(), rotate(), and scale() as desired ...
		
		// draw the mesh defined by our custom OBJMAP entry
		drawObj(0);
	popMatrix();
}
```

!!! info
	Although `OBJMAP` entries can be created in code, they can also be automatically filled in when importing a model file using the model editor.

#### `WAVMAP`

Address range: `0x00F63854-0x00F65853`

Accessible using constant `MEMORY_WAVMAP`.

Contains a table of 512 user-defined audio wave objects.

Each entry in the `WAVMAP` consists of 4 32-bit `int` values, detailed in the following table:

`int` Index | Description
-|-
0 | Sample start index
1 | Sample end index (inclusive)
2 | Loop start index
3 | Loop end index (inclusive)

Audio sample data is stored in [`WAVMEM`](#wavmem), and is read by the soundchip when playing sounds.

Sample start and sample end define the range of samples to play when a sound is triggered.

Loop start and loop end define a sample range to loop when a sound is played using the Range looping mode.

The following diagram illustrates how this works:

```

no looping (normal playback):

        sample start               sample end
        v                          v
sound: [>>>>>>>>>>>>>>>>>>>>>>>>>>>>]

the whole sound is played once.

---------------------------------------------

range looping:

        sample start               sample end
        v                          v
sound: [>>>>>>|>>>>>>>>>>>>|--------]
              ^            ^
              loop start   loop end

the sound is played until loop end,
then playback jumps back to loop start.
```

`WAVMAP` entries can be used by tracker instruments to play specific sample ranges from `WAVMEM`, as well as by the user for playback using the `playWav()` API function.

```C
void init() {
	// configure a custom WAVMAP entry.
	// suppose we have a sound effect loaded in WAVMEM from sample indices 0x000 to 0x1FF that we want to play,
	// when range looping is used we want to loop from 0x100 to 0x1FF
	
	// get a pointer to the first WAVMAP entry (entry index 0)
	int* wavmap_ptr = MEMORY_WAVMAP;
	
	// set WAVMAP entry values
	wavmap_ptr[0] = 0x000; // sample start
	wavmap_ptr[1] = 0x1FF; // sample end
	wavmap_ptr[2] = 0x100; // loop start
	wavmap_ptr[3] = 0x1FF; // loop end
}

void update(float delta_time) {
	// play the wave defined by our custom WAVMAP entry on track 0 at 80% volume (no looping)
	if (should_play_sound) {
		playWav(
			0, // track index
			0, // WAVMAP entry index
			0nC4, // play at note C in octave 4 (default pitch)
			80.0, // volume
			LOOP_OFF // loop mode
		);
	}
}
```

!!! info
	Although `WAVMAP` entries can be created in code, they can also be automatically filled in when importing an audio file using the tracker.

#### 3D Cameras

Address range: `0x00F65854-0x00F65903`

Contains the 4 built-in 3D cameras.

To get a pointer to a 3D camera, use the `getCam3D()` API function.

```C
cam3d* cam = getCam3D(0); // get a pointer to 3D camera 0
```

#### 2D Cameras

Address range: `0x00F65904-0x00F65963`

Contains the 4 built-in 2D cameras.

To get a pointer to a 2D camera, use the `getCam2D()` API function.

```C
cam2d* cam = getCam2D(0); // get a pointer to 2D camera 0
```

#### Lights

Address range: `0x00F65964-0x00F65AA3`

Contains the 8 built-in lights.

To get a pointer to a light, use the `getLight()` API function.

```C
light* light0 = getLight(0); // get a pointer to light 0
```

#### GPU State

Address range: `0x00F65AA4-0x00FFFFFF`

TODO

### `WAVMEM`

Address range: `0x01000000-0x016FFFFF`

Accessible using constant `MEMORY_WAVMEM`.

Contains the currently loaded audio data.

Audio samples stored in `WAVMEM` are 16-bit signed integer values that come in pairs for stereo audio.

Samples are arranged such that:

- The first 16-bit value is the first sample for the left speaker
- The second value is the first sample for the right speaker
- The third value is the second sample for the left speaker

and so on.

Audio in `WAVMEM` is played at a sample rate of 22050hz.

There is enough space for roughly 1 minute and 23 seconds of audio data (1835008 sample pairs, to be exact) to be loaded at once.

In other words, sample pair indices range from `0x000000` to `0x1BFFFF`.

ERA-C does not have a built-in 16-bit integer type, but the data in `WAVMEM` can be treated as an array of `int` values.

When used this way, each `int` in `WAVMEM` will contain a combined left + right sample pair.

```C
// suppose we have a sound effect loaded in ROM that is 0x1FF sample pairs in length,
// and we want to copy it into WAVMEM at a sample pair index of 0x2000.

int offset = 0x2000;

// pointer to the sound effect in ROM
int* rom_ptr = address_of_sfx_in_rom;

// get offset pointer to WAVMEM,
// the cast is needed here to get the correct offset
int* wave_data = ((int*)MEMORY_WAVMEM) + offset;

// copy the sound effect into WAVMEM;
// we multiply 0x1FF by 2 to get the number of bytes to copy
memcpy(wave_data, rom_ptr, 0x1FF * 2);
```

Audio stored in `WAVMEM` can be played directly using the `playWav()` and `playWavEx()` API functions.

`playWav()` uses the [Wave Map (`WAVMAP`)](#wavmap) to play a predefined wave. (The `WAVMAP` is detailed in the `SYSMEM` section.)

```C
void update(float delta_time) {
	// play the wave defined by WAVMAP entry 0 on track 0 at 80% volume (no looping)
	if (should_play_sound) {
		playWav(
			0, // track index
			0, // WAVMAP entry index
			0nC4, // play at note C in octave 4 (default pitch)
			80.0, // volume
			LOOP_OFF // loop mode
		);
	}
}
```

`playWavEx()` accepts parameters to control which samples from `WAVMEM` are played, as well as a custom loop range.

```C
void update(float delta_time) {
	// play the first 0x1FF sample pairs in WAVMEM on track 0 at 80% volume (no looping)
	if (should_play_sound) {
		playWavEx(
			0, // track index
			0, // sample start index
			0x1FF, // sample end index (inclusive)
			0, // loop start index
			0, // loop end index (inclusive)
			0nC4, // play at note C in octave 4 (default pitch)
			80.0, // volume
			LOOP_OFF // loop mode
		);
	}
}
```

### `SEQMEM`

Address range: `0x01700000-0x0173FFFF`

Accessible using constant `MEMORY_SEQMEM`.

Contains the currently loaded soundchip sequencer (tracker) data.

`SEQMEM` is divided into multiple sub-regions, which are detailed below.

#### Song Data

Address range: `0x01700000-0x017007FF`

Contains the audio sequencer song data.

#### Pattern Data

Address range: `0x01700800-0x17147FF`

Contains the audio sequencer pattern data.

#### Instrument Data

Address range: `0x01714800-0x017160FF`

Contains the audio sequencer instrument data.

#### Groove Data

Address range: `0x01716100-0x0173FFFF`

Contains the audio sequencer groove data.

### `GLOBALS`

Address range: `0x01740000-0x0177FFFF`

Contains VM global variables.

Getting the address of a global variable will result in a pointer to this region.

### `LOCALS`

Address range: `0x01780000-0x017BFFFF`

Contains VM local variables.

Getting the address of a local variable will result in a pointer to this region.

### `ARGS`

Address range: `0x017C0000-0x017FFFFF`

Contains VM function arguments.

Getting the address of a function argument will result in a pointer to this region.

## Cartridge ROM

Cartridge ROM is the region of memory that contains all data mapped to the currently loaded cartridge.

Data in this memory region is read-only.

### `TEXBANK`s

Address range: `0x01800000-0x027FFFFF`

Accessible using constants `MEMORY_TEXBANK0` to `MEMORY_TEXBANK3`.

Contains 4 texture data banks, reffered to as Texture Banks.

Each Texture Bank has the same size and format as [`TEXMEM`](#texmem).

The [`loadTexBank()` API function](api-reference.md#loadtexbank) can be used to load a Texture Bank into `TEXMEM`.

```C
loadTexBank(0); // load TEXBANK0 into TEXMEM
```

### `OBJBANK`s

Address range: `0x02800000-0x0357FFFF`

Accessible using constants `MEMORY_OBJBANK0` to `MEMORY_OBJBANK3`.

Contains 4 mesh data banks, reffered to as Object Banks.

Each Object Bank has the same size and format as [`OBJMEM`](#objmem).

The [`loadObjBank()` API function](api-reference.md#loadobjbank) can be used to load an Object Bank into `OBJMEM`.

```C
loadTexBank(0); // load OBJBANK0 into OBJMEM
```

`loadObjBank()` will also load the associated Object Map Bank (`OMPBANK`) into the [Object Map (`OBJMAP`)](#objmap).

### `OMPBANK`s

Address range: `0x03580000-0x036BFFFF`

Accessible using constants `MEMORY_OMPBANK0` to `MEMORY_OMPBANK3`.

Contains 4 Object Maps.

Each Object Map Bank has the same size and format as [`OBJMAP`](#objmap), and is associated with the Object Bank with the same ID.

### `WMPBANK`s

Address range: `0x036C0000-0x037FFFFF`

Accessible using constants `MEMORY_WMPBANK0` and `MEMORY_WMPBANK1`.

Contains 4 Wave Maps.

Each Wave Map Bank has the same size and format as [`WAVMAP`](#wavmap), and is associated with the Wave Bank with the same ID.

### `WAVBANK`s

Address range: `0x03800000-0x045FFFFF`

Accessible using constants `MEMORY_WAVBANK0` and `MEMORY_WAVBANK1`.

Contains 2 audio data banks, reffered to as Wave Banks.

Each Wave Bank has the same size and format as [`WAVMEM`](#wavmem).

The [`loadWavBank()` API function](api-reference.md#loadwavbank) can be used to load a Wave Bank into `WAVMEM`.

```C
loadWavBank(0); // load WAVBANK0 into WAVMEM
```

`loadWavBank()` will also load the associated Wave Map Bank (`WMPBANK`) into the [Wave Map (`WAVMAP`)](#wavmap).

### `SEQBANK`s

Address range: `0x04600000-0x047FFFFF`

Accessible using constants `MEMORY_SEQBANK0` to `MEMORY_SEQBANK7`.

Contains 8 audio sequencer data banks, reffered to as Sequence Banks.

Each Sequence Bank has the same size and format as [`SEQMEM`](#seqmem).

The [`loadSeqBank()` API function](api-reference.md#loadseqbank) can be used to load a Sequence Bank into `SEQMEM`.

```C
loadSeqBank(0); // load SEQBANK0 into SEQMEM
```

### `ROM`

Address range: `0x04800000-0x057FFFFF`

Accessible using constant `MEMORY_ROM`.

Contains string literal data and user ROM data.

!!! warning
	Currently, the ERA-C compiler starts at the beginning of `ROM` and writes string literal data as the cart's code is compiled.

	This will overwrite any ROM data that might be stored there.

	The compiler will also repeat string literals in ROM if identical strings are encountered.

	Facilities for reusing strings, customizing the starting address for string data, as well as uploading custom ROM data are all planned.

## Memory Card

The memory card is a region of memory that contains persistent save data.

Data in this memory region can be read from and written to once the `initMemCard()` API function is called.

See the [API reference for `initMemCard()`](api-reference.md#initmemcard) for details.

### `MEMCARD`

Address range: `0x05800000-0x05800FFF`

Accessible using constant `MEMORY_MEMCARD`.

Data written here will be saved to a file that can be loaded later using the same cart ID.

The user is free to use this memory in any way they see fit.

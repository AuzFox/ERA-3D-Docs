# Memory Map

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
`TEXBANK[0-3]`    | `16MiB`          | `0x01800000-0x027FFFFF` | 4x texture sheets
`OBJBANK[0-3]`    | `13MiB + 512KiB` | `0x02800000-0x0357FFFF` | 4x mesh data buffers
`OMPBANK[0-3]`    | `1MiB + 256KiB`  | `0x03580000-0x036BFFFF` | 4x maps for OBJBANK[0-3]
`WMPBANK[0-1]`    | `1MiB + 256KiB`  | `0x036C0000-0x037FFFFF` | 2x maps for WAVBANK[0-1]
`WAVBANK[0-1]`    | `14MiB`          | `0x03800000-0x045FFFFF` | 2x wave data buffers
`SEQBANK[0-7]`    | `2MiB`           | `0x04600000-0x047FFFFF` | 8x audio sequencer data buffers
`ROM`             | `16MiB`          | `0x04800000-0x057FFFFF` | String data + user ROM
__Memory Card__   |                  |                         |
`MEMCARD`         | `4KiB`           | `0x05800000-0x05800FFF` | Persistent save data

## System Memory

TODO

### `HEAP`

todo

### `TEXMEM`

todo

### `OBJMEM`

todo

### `AOBMEM`

todo

### `SYSMEM`

todo

### `WAVMEM`

todo

### `SEQMEM`

todo

### `GLOBALS`

todo

### `LOCALS`

todo

### `ARGS`

todo

## Cartridge ROM

todo

### `TEXBANK[0-3]`

todo

### `OBJBANK[0-3]`

todo

### `OMPBANK[0-3]`

todo

### `WMPBANK[0-1]`

todo

### `WAVBANK[0-1]`

todo

### `SEQBANK[0-7]`

todo

### `ROM`

todo

## Memory Card

todo

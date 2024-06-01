# API Reference

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

## Introduction

This page contains documentation for all of ERA-3D's API Functions.

!!! info
	A brief description of each function can be accessed using the ERA-3D console.
	
	Access the console by pressing ++ctrl+enter++.

	The console command `api` will open a list of API functions, use the arrow keys to navigate and press ++enter++ to view a function's description.

	To quickly get the description of a specific function, run the console command `help <function>`.

## Function Catagories

API functions are organized into several catagories, click a catagory below or in the sidebar to jump to the related functions.

You can also use the search bar in the site header to search for a particular function.

- [Math](#math)
- [Vectors](#vectors)
- [Matrices](#matrices)
- [Input](#input)
- [Graphics](#graphics)
- [Audio](#audio)
- [Physics](#physics)
- [Memory](#memory)
- [Misc](#misc)

## Math

### `ceil`

!!! info ""
	__Signature__:

	`#!c float ceil(float x)`

	__Arguments__:

	- `#!c float x: Input value`

	__Description__:

	Returns __x__ rounded upward to the nearest whole number.
	This function always rounds toward positive infinity.

### `cos`

!!! info ""
	__Signature__:

	`#!c float cos(float x)`

	__Arguments__:

	- `#!c float x: Input value`

	__Description__:

	Returns the cosine of __x__.
	Return value ranges from -1.0 to 1.0.

### `deg`

!!! info ""
	__Signature__:

	`#!c float deg(float angle)`

	__Arguments__:

	- `#!c float angle: Input angle (in radians)`

	__Description__:

	Returns __angle__ in degrees.

### `floor`

!!! info ""
	__Signature__:

	`#!c float floor(float x)`

	__Arguments__:

	- `#!c float x: Input value`

	__Description__:

	Returns __x__ rounded downward to the nearest whole number.
    This function always rounds toward negative infinity.

### `fract`

!!! info ""
	__Signature__:

	`#!c float fract(float x)`

	__Arguments__:

	- `#!c float x: The value to get the fractional component of`

	__Description__:

	Returns the fractional component of __x__.

### `maxf`

!!! info ""
	__Signature__:

	`#!c float maxf(float a, float b)`

	__Arguments__:

	- `#!c float a: The first value to check`
	- `#!c float b: The second value to check`

	__Description__:

	Returns the higher of the two given floats.

### `maxi`

!!! info ""
	__Signature__:

	`#!c int maxi(int a, int b)`

	__Arguments__:

	- `#!c int a: The first value to check`
	- `#!c int b: The second value to check`

	__Description__:

	Returns the higher of the two given integers.

### `midf`

!!! info ""
	__Signature__:

	`#!c float midf(float a, float b, float c)`

	__Arguments__:

	- `#!c float a: The first value to check`
	- `#!c float b: The second value to check`
	- `#!c float c: The third value to check`

	__Description__:

	Returns the middle of the three given floats.

### `midi`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `minf`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `mini`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `powf`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `rad`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `randfEx`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `randf`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `randiEx`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `randi`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `randomizeEx`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `randomize`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `round`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `signf`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `signi`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `sin`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `wrapf`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...

### `wrapi`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`

	__Description__:

	...


## Vectors

### `cam3DForward`
### `cam3DRight`
### `vec2Angle`
### `vec2Cross`
### `vec2Direction`
### `vec2DistanceSq`
### `vec2Distance`
### `vec2Dot`
### `vec2Down`
### `vec2Invert`
### `vec2Left`
### `vec2LengthSq`
### `vec2Length`
### `vec2Lerp`
### `vec2MoveToward`
### `vec2Normalize`
### `vec2One`
### `vec2Reflect`
### `vec2Right`
### `vec2Rotate`
### `vec2Up`
### `vec2Zero`
### `vec3Angle`
### `vec3Back`
### `vec3Cross`
### `vec3Direction`
### `vec3DistanceSq`
### `vec3Distance`
### `vec3Dot`
### `vec3Down`
### `vec3Forward`
### `vec3Invert`
### `vec3Left`
### `vec3LengthSq`
### `vec3Length`
### `vec3Lerp`
### `vec3MoveToward`
### `vec3Normalize`
### `vec3One`
### `vec3Reflect`
### `vec3Right`
### `vec3Rotate`
### `vec3ToScreen`
### `vec3Up`
### `vec3Zero`

## Matrices

### `matrixAdd`
### `matrixIdentity`
### `matrixInvert`
### `matrixLookAt`
### `matrixMultiply`
### `matrixRotate`
### `matrixScale`
### `matrixSubtract`
### `matrixTranslate`
### `matrixTranspose`

## Input

### `getMouseDelta`
### `getMouseDrag`
### `getMouseLock`
### `getMousePosition`
### `getMouseWheel`
### `held`
### `mouseDragging`
### `mouseHeld`
### `mousePressed`
### `mouseReleased`
### `pressed`
### `released`
### `setMouseLock`

## Graphics

### `ambientColor`
### `ambientFactor`
### `beginMesh`
### `blendFactors`
### `blendFactorsEx`
### `blendMode`
### `camera2D`
### `camera3D`
### `clear`
### `clearColor`
### `clearDepth`
### `clearStencil`
### `colorMask`
### `cullMode`
### `depthFunc`
### `depthMask`
### `depthTest`
### `drawObj`
### `drawObjEx`
### `endMesh`
### `fogColor`
### `fogEnd`
### `fogMode`
### `fogStart`
### `frustum`
### `getCam2D`
### `getCam3D`
### `getLight`
### `getModelViewMatrix`
### `getProjectionMatrix`
### `getTopMatrix`
### `identity`
### `lightingMode`
### `lookAt`
### `meshColor`
### `meshNormal`
### `meshUV`
### `meshVertex`
### `meshVertex2D`
### `multiplyTopMatrix`
### `ortho`
### `popMatrix`
### `print2D`
### `pushMatrix`
### `rotate`
### `scale`
### `scissor`
### `scissorMode`
### `setModelViewMatrix`
### `setProjectionMatrix`
### `sprite2D`
### `sprite2DEx`
### `stencilFunc`
### `stencilMask`
### `stencilMode`
### `stencilOp`
### `texture`
### `textureMode`
### `translate`
### `viewport`
### `wireMode`

## Audio

### `getTrackBPM`
### `getTrackPan`
### `getTrackVolume`
### `muteTracks`
### `muteTrack`
### `pauseTracks`
### `pauseTrack`
### `playPattern`
### `playSong`
### `playTrack`
### `playWavEx`
### `playWav`
### `resumeTracks`
### `resumeTrack`
### `setTrackBPM`
### `setTrackPan`
### `setTrackVolume`
### `stopTracks`
### `stopTrack`
### `unmuteTracks`
### `unmuteTrack`

## Physics

### `checkCollision`
### `getRaycastNormal`
### `getRaycastPoint`
### `raycast`

## Memory

### `initMemCard`
### `loadObjBank`
### `loadSeqBank`
### `loadTexBank`
### `loadWavBank`
### `memcpy`
### `memset`
### `peek8`
### `peek32`
### `poke8`
### `poke32`

## Misc

### `time`
### `vargc`
### `vargv`

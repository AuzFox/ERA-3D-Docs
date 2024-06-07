# API Reference

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

	- `#!c float x`: Input value

	__Description__:

	Returns __x__ rounded upward to the nearest whole number.
	This function always rounds toward positive infinity.

### `cos`

!!! info ""
	__Signature__:

	`#!c float cos(float x)`

	__Arguments__:

	- `#!c float x`: Input value

	__Description__:

	Returns the cosine of __x__.
	Return value ranges from `#!c -1.0` to `#!c 1.0`.

### `deg`

!!! info ""
	__Signature__:

	`#!c float deg(float angle)`

	__Arguments__:

	- `#!c float angle`: Input angle (in radians)

	__Description__:

	Returns __angle__ in degrees.

### `floor`

!!! info ""
	__Signature__:

	`#!c float floor(float x)`

	__Arguments__:

	- `#!c float x`: Input value

	__Description__:

	Returns __x__ rounded downward to the nearest whole number.
    This function always rounds toward negative infinity.

### `fract`

!!! info ""
	__Signature__:

	`#!c float fract(float x)`

	__Arguments__:

	- `#!c float x`: The value to get the fractional component of

	__Description__:

	Returns the fractional component of __x__.

### `maxf`

!!! info ""
	__Signature__:

	`#!c float maxf(float a, float b)`

	__Arguments__:

	- `#!c float a`: The first value to check
	- `#!c float b`: The second value to check

	__Description__:

	Returns the higher of the two given floats.

### `maxi`

!!! info ""
	__Signature__:

	`#!c int maxi(int a, int b)`

	__Arguments__:

	- `#!c int a`: The first value to check
	- `#!c int b`: The second value to check

	__Description__:

	Returns the higher of the two given integers.

### `midf`

!!! info ""
	__Signature__:

	`#!c float midf(float a, float b, float c)`

	__Arguments__:

	- `#!c float a`: The first value to check
	- `#!c float b`: The second value to check
	- `#!c float c`: The third value to check

	__Description__:

	Returns the middle of the three given floats.

### `midi`

!!! info ""
	__Signature__:

	`#!c int midi(int a, int b, int c)`

	__Arguments__:

	- `#!c int a`: The first value to check
	- `#!c int b`: The second value to check
	- `#!c int c`: The third value to check

	__Description__:

	Returns the middle of the three given integers.

### `minf`

!!! info ""
	__Signature__:

	`#!c float minf(float a, float b)`

	__Arguments__:

	- `#!c float a`: The first value to check
	- `#!c float b`: The second value to check

	__Description__:

	Returns the lower of the two given floats.

### `mini`

!!! info ""
	__Signature__:

	`#!c int mini(int a, int b)`

	__Arguments__:

	- `#!c int a`: the first value to check
    - `#!c int b`: the second value to check

	__Description__:

	Returns the lower of the two given integers.

### `powf`

!!! info ""
	__Signature__:

	`#!c float powf(float x, float exp)`

	__Arguments__:

	- `#!c float x`: The base value
	- `#!c float exp`: The exponent value

	__Description__:

	Returns __x__ raised to the power of __exp__.

### `rad`

!!! info ""
	__Signature__:

	`#!c float rad(float angle)`

	__Arguments__:

	- `#!c float angle`: Input angle (in degrees)

	__Description__:

	Returns __angle__ in radians.

### `randf`

!!! info ""
	__Signature__:

	`#!c float randf(float min, float max)`

	__Arguments__:

	- `#!c float min`: The minimum range value (inclusive)
	- `#!c float max`: The maximum range value (inclusive)

	__Description__:

	Returns a random `float` in the range [__min__, __max__].

### `randfEx`

!!! info ""
	__Signature__:

	`#!c float randfEx()`

	__Description__:

	Returns a random `float` in the range [0.0, 1.0).

### `randi`

!!! info ""
	__Signature__:

	`#!c int randi(int min, int max)`

	__Arguments__:

	- `#!c int min`: The minimum range value (inclusive)
	- `#!c int max`: The maximum range value (inclusive)

	__Description__:

	Returns a random `int` in the range [__min__, __max__].

### `randiEx`

!!! info ""
	__Signature__:

	`#!c int randiEx()`

	__Description__:

	Returns an `int` with individually randomized bits.

### `randomize`

!!! info ""
	__Signature__:

	`#!c void randomize()`

	__Description__:

	Initializes the random number generator with a weak seed.

    It is not strictly necessary to call this function on init, as the system will initialize RNG when a cart is ran.

### `randomizeEx`

!!! info ""
	__Signature__:

	`#!c void randomizeEx(int seed)`

	__Arguments__:

	- `#!c int seed`: Initialization value for RNG

	__Description__:

	Initializes the random number generator with __seed__.
	
	Identical seeds will produce the same sequence of numbers.

### `round`

!!! info ""
	__Signature__:

	`#!c float round(float x)`

	__Arguments__:

	- `#!c float x`: Input value

	__Description__:

	Returns __x__ rounded toward to the nearest whole number.
    
	Halfway cases are rounded away from zero.

### `signf`

!!! info ""
	__Signature__:

	`#!c float signf(float x)`

	__Arguments__:

	- `#!c float x`: Input value

	__Description__:

	Returns the sign of the `float` __x__.
    
    If __x__ < 0, returns -1.

    If __x__ > 0, returns 1.

    If __x__ == 0, returns 0.

### `signi`

!!! info ""
	__Signature__:

	`#!c int signi(int x)`

	__Arguments__:

	- `#!c int x`: Input value

	__Description__:

	Returns the sign of the `int` __x__.
    
    If __x__ < 0, returns -1.

    If __x__ > 0, returns 1.

    If __x__ == 0, returns 0.

### `sin`

!!! info ""
	__Signature__:

	`#!c float sin(float x)`

	__Arguments__:

	- `#!c float x`: Input value

	__Description__:

	Returns the sine of __x__.

    Return value will be in the range [-1.0, 1.0].

### `wrapf`

!!! info ""
	__Signature__:

	`#!c float wrapf(float x, float min, float max)`

	__Arguments__:

	- `#!c float x`: The value to wrap
	- `#!c float min`: The minimum range value
	- `#!c float max`: The maximum range value (exclusive)

	__Description__:

	Returns a `float` value within the range [__min__, __max__).

    If __x__ is < __min__ or __x__ >= __max__, it wraps around to the other end of the range.

### `wrapi`

!!! info ""
	__Signature__:

	`#!c int wrapi(int x, int min, int max)`

	__Arguments__:

	- `#!c int x`: The value to wrap
	- `#!c int min`: The minimum range value
	- `#!c int max`: The maximum range value (exclusive)

	__Description__:

	Returns an `int` value within the range [__min__, __max__).

    If __x__ is < __min__ or __x__ >= __max__, it wraps around to the other end of the range.

## Vectors

### `cam3DForward`

!!! info ""
	__Signature__:

	`#!c vec3 cam3DForward(int camera)`

	__Arguments__:

	- `#!c int camera`: Index of the 3D camera to use [0-3]
	
	__Description__:

	Returns a 3D vector pointing forward in __camera__'s local space.

### `cam3DRight`

!!! info ""
	__Signature__:

	`#!c vec3 cam3DRight(int camera)`

	__Arguments__:

	- `#!c int camera`: Index of the 3D camera to use [0-3]
	
	__Description__:

	Returns a 3D vector pointing rightward in __camera__'s local space.

### `vec2Angle`

!!! info ""
	__Signature__:

	`#!c float vec2Angle(vec2 a, vec2 b)`

	__Arguments__:

	- `#!c vec2 a`: First input vector
	- `#!c vec2 b`: Second input vector
	
	__Description__:

	Returns the angle (in degrees) from __a__ to __b__.

### `vec2Cross`

!!! info ""
	__Signature__:

	`#!c float vec2Cross(vec2 a, vec2 b)`

	__Arguments__:

	- `#!c vec2 a`: First input vector
	- `#!c vec2 b`: Second input vector
	
	__Description__:

	Returns the cross product of __a__ and __b__.

	This value is computed as `#!c (a.x * b.y - a.y * b.x)`.

### `vec2Direction`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Direction(vec2 a, vec2 b)`

	__Arguments__:

	- `#!c vec2 a`: Start vector
	- `#!c vec2 b`: End vector
	
	__Description__:

	Returns a normalized 2D vector pointing from __a__ to __b__.

### `vec2Distance`

!!! info ""
	__Signature__:

	`#!c float vec2Distance(vec2 a, vec2 b)`

	__Arguments__:

	- `#!c vec2 a`: First input vector
	- `#!c vec2 b`: Second input vector
	
	__Description__:

	Returns the distance between __a__ and __b__.

### `vec2DistanceSq`

!!! info ""
	__Signature__:

	`#!c float vec2DistanceSq(vec2 a, vec2 b)`

	__Arguments__:

	- `#!c vec2 a`: First input vector
	- `#!c vec2 b`: Second input vector
	
	__Description__:

	Returns the squared distance between __a__ and __b__.

	This function is less costly to compute than `vec2Distance()`.

	As such, it is recommended to use this function when exact distance is not needed.

### `vec2Dot`

!!! info ""
	__Signature__:

	`#!c float vec2Dot(vec2 a, vec2 b)`

	__Arguments__:

	- `#!c vec2 a`: First input vector
	- `#!c vec2 b`: Second input vector
	
	__Description__:

	Returns the dot product of __a__ and __b__.

	Use this function to compare the angle between two 2D vectors.

	For un-normalized vectors:

	- Returns 0 when the angle is 90 degrees
	- Returns a negative value when the angle is greater than 90 degrees
	- Returns a positive value when the angle is less than 90 degrees

	For normalized vectors:

	- Returns a value in the range [-1.0, 1.0]; -1.0 for a 180 degree angle and 1.0 when __a__ and __b__ are aligned.

### `vec2Down`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Down()`

	__Description__:

	Returns a `vec2` with the value `vec2(0.0, -1.0)`.

### `vec2Invert`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Invert(vec2 v)`

	__Arguments__:

	- `#!c vec2 v`: The vector to invert
	
	__Description__:

	Returns the inverse of the __v__.

	Equivelent to `vec2(1.0 / v.x, 1.0 / v.y)`.

### `vec2Left`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Left()`

	__Description__:

	Returns a `vec2` with the value `vec2(-1.0, 0.0)`.

### `vec2Length`

!!! info ""
	__Signature__:

	`#!c float vec2Length(vec2 v)`

	__Arguments__:

	- `#!c vec2 v`: The vector to get the length of
	
	__Description__:

	Returns the length (magnitude) of __v__.

### `vec2LengthSq`

!!! info ""
	__Signature__:

	`#!c float vec2LengthSq(vec2 v)`

	__Arguments__:

	- `#!c vec2 v`: The vector to get the length of
	
	__Description__:

	Returns the squared length (squared magnitude) of __v__.

	This function is less costly to compute than vec2length().

	As such, it is recommended to use this function when exact magnitude is not needed. (i.e. comparing vectors)

### `vec2Lerp`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Lerp(vec2 start, vec2 end, float amount)`

	__Arguments__:

	- `#!c vec2 start`: Start vector
	- `#!c vec2 end`: Destination vector
	- `#!c float amount`: Amount to interpolate by (1.0 = 100%)
	
	__Description__:

	Returns the linear interpolation between __start__ and __end__.

### `vec2MoveToward`

!!! info ""
	__Signature__:

	`#!c vec2 vec2MoveToward(vec2 start, vec2 end, float distance)`

	__Arguments__:

	- `#!c vec2 start`: Starting vector
	- `#!c vec2 end`: Destination vector
	- `#!c float distance`: Maximum distance to travel
	
	__Description__:

	Returns the 2D vector __start__ after being moved toward __end__ by the given __distance__.

	If __distance__ is greater than the amount required to reach __end__, returns __end__.

### `vec2Normalize`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Normalize(vec2 v)`

	__Arguments__:

	- `#!c vec2 v`: The vector to normalize
	
	__Description__:

	Returns a 2D vector that points in the same direction as __v__, but has a length (magnitude) of 1.0.

### `vec2One`

!!! info ""
	__Signature__:

	`#!c vec2 vec2One()`

	__Description__:

	Returns a `vec2` with the value `vec2(1.0, 1.0)`.

### `vec2Reflect`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Reflect(vec2 v, vec2 normal)`

	__Arguments__:

	- `#!c vec2 v`: The vector to reflect
	- `#!c vec2 normal`: The normal vector to reflect off of
	
	__Description__:

	Returns the 2D vector __v__ reflected off of the __normal__ vector.

### `vec2Right`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Right()`

	__Description__:

	Returns a `vec2` with the value `vec2(1.0, 0.0)`.

### `vec2Rotate`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Rotate(vec2 v, float angle)`

	__Arguments__:

	- `#!c vec2 v`: The starting vector
	- `#!c vec2 angle`: The angle to rotate by (in degrees)
	
	__Description__:

	Returns the 2D vector __v__ rotated by the given __angle__.

### `vec2Up`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Up()`

	__Description__:

	Returns a `vec2` with the value `vec2(0.0, 1.0)`.

### `vec2Zero`

!!! info ""
	__Signature__:

	`#!c vec2 vec2Zero()`

	__Description__:

	Returns a `vec2` with the value `vec2(0.0, 0.0)`.

### `vec3Angle`

!!! info ""
	__Signature__:

	`#!c float vec3Angle(vec3 a, vec3 b)`

	__Arguments__:

	- `#!c vec3 a`: First input vector
	- `#!c vec3 b`: Second input vector
	
	__Description__:

	Returns the angle (in degrees) from __a__ to __b__.

### `vec3Back`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Back()`

	__Description__:

	Returns a `vec3` with the value `vec3(0.0, 0.0, 1.0)`.

### `vec3Cross`

!!! info ""
	__Signature__:

	`#!c float vec3Cross(vec3 a, vec3 b)`

	__Arguments__:

	- `#!c vec3 a`: First input vector
	- `#!c vec3 b`: Second input vector
	
	__Description__:

	Returns the cross product of __a__ and __b__.

### `vec3Direction`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Direction(vec3 a, vec3 b)`

	__Arguments__:

	- `#!c vec3 a`: Start vector
	- `#!c vec3 b`: End vector
	
	__Description__:

	Returns a normalized 3D vector pointing from __a__ to __b__.

### `vec3Distance`

!!! info ""
	__Signature__:

	`#!c float vec3Distance(vec3 a, vec3 b)`

	__Arguments__:

	- `#!c vec3 a`: First input vector
	- `#!c vec3 b`: Second input vector
	
	__Description__:

	Returns the distance between __a__ and __b__.

### `vec3DistanceSq`

!!! info ""
	__Signature__:

	`#!c float vec3DistanceSq(vec3 a, vec3 b)`

	__Arguments__:

	- `#!c vec3 a`: First input vector
	- `#!c vec3 b`: Second input vector
	
	__Description__:

	Returns the squared distance between __a__ and __b__.

	This function is less costly to compute than `vec3Distance()`.

	As such, it is recommended to use this function when exact distance is not needed.

### `vec3Dot`

!!! info ""
	__Signature__:

	`#!c float vec3Dot(vec3 a, vec3 b)`

	__Arguments__:

	- `#!c vec3 a`: First input vector
	- `#!c vec3 b`: Second input vector
	
	__Description__:

	Returns the dot product of __a__ and __b__.

	Use this function to compare the angle between two 3D vectors.

	For un-normalized vectors:

	- Returns 0 when the angle is 90 degrees.
	- Returns a negative value when the angle is greater than 90 degrees.
	- Returns a positive value when the angle is less than 90 degrees.

	For normalized vectors:

	- Returns a value in the range [-1.0, 1.0]; -1.0 for a 180 degree angle and 1.0 when __a__ and __b__ are aligned.

### `vec3Down`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Down()`

	__Description__:

	Returns a `vec3` with the value `vec3(0.0, 1.0, 0.0)`.

### `vec3Forward`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Forward()`

	__Description__:

	Returns a `vec3` with the value `vec3(0.0, 0.0, -1.0)`.

### `vec3Invert`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Invert(vec3 v)`

	__Arguments__:

	- `#!c vec3 v`: The vector to invert
	
	__Description__:

	Returns the inverse of __v__.

	Equivelent to `vec3(1.0 / v.x, 1.0 / v.y, 1.0 / v,z)`.

### `vec3Left`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Left()`

	__Description__:

	Returns a `vec3` with the value `vec3(-1.0, 0.0, 0.0)`.

### `vec3Length`

!!! info ""
	__Signature__:

	`#!c float vec3Length(vec3 v)`

	__Arguments__:

	- `#!c vec3 v`: The vector to get the length of
	
	__Description__:

	Returns the length (magnitude) of __v__.

### `vec3LengthSq`

!!! info ""
	__Signature__:

	`#!c float vec3LengthSq(vec3 v)`

	__Arguments__:

	- `#!c vec3 v`: The vector to get the length of
	
	__Description__:

	Returns the squared length (squared magnitude) of __v__.

	This function is less costly to compute than `vec3Length()`.

	As such, it is recommended to use this function when exact magnitude is not needed. (i.e. comparing vectors)

### `vec3Lerp`

!!! info ""
	__Signature__:

	`#!c vec2 vec3Lerp(vec3 start, vec3 end, float amount)`

	__Arguments__:

	- `#!c vec3 start`: Start vector
	- `#!c vec3 end`: Destination vector
	- `#!c float amount`: Amount to interpolate by (1.0 = 100%)
	
	__Description__:

	Returns the linear interpolation between __start__ and __end__.

### `vec3MoveToward`

!!! info ""
	__Signature__:

	`#!c vec3 vec3MoveToward(vec3 start, vec3 end, float distance)`

	__Arguments__:

	- `#!c vec3 start`: The starting vector
	- `#!c vec3 end`: The destination vector
	- `#!c float distance`: The maximum distance to travel
	
	__Description__:

	Returns the 3D vector __start__ after being moved toward __end__ by the given __distance__.

	If __distance__ is greater than the amount required to reach __end__, returns __end__.

### `vec3Normalize`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Normalize(vec3 v)`

	__Arguments__:

	- `#!c vec3 v`: The vector to normalize
	
	__Description__:

	Returns a 3D vector that points in the same direction as __v__, but has a length (magnitude) of 1.0.

### `vec3One`

!!! info ""
	__Signature__:

	`#!c vec3 vec3One()`

	__Description__:

	Returns a `vec3` with the value `vec3(1.0, 1.0, 1.0)`.

### `vec3Reflect`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Reflect(vec3 v, vec3 normal)`

	__Arguments__:

	- `#!c vec3 v`: The vector to reflect
	- `#!c vec3 normal`: The normal vector to reflect off of
	
	__Description__:

	Returns the 3D vector __v__ reflected off of the __normal__ vector.

### `vec3Right`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Right()`

	__Description__:

	Returns a `vec3` with the value `vec3(1.0, 0.0, 0.0)`.

### `vec3Rotate`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Rotate(vec3 v, vec3 axis, float angle)`

	__Arguments__:

	- `#!c vec2 v`: The starting vector
	- `#!c vec2 axis`: The axis to rotate along
	- `#!c vec2 angle`: The angle to rotate by (in degrees)
	
	__Description__:

	Returns the 3D vector __v__ rotated along the given __axis__ by the given __angle__.

### `vec3ToScreen`

!!! info ""
	__Signature__:

	`#!c vec2 vec3ToScreen(vec3 v, int camera)`

	__Arguments__:

	- `#!c vec3 v`: The vector to project
	- `#!c int camera`: The index of the 3D camera to use for the projection [0-3]
	
	__Description__:

	Returns a 2D vector containing the screen coordinates of the 3D vector __v__, as viewed from the perspective of the given 3D __camera__.

### `vec3Up`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Up()`

	__Description__:

	Returns a `vec3` with the value `vec3(0.0, -1.0, 0.0)`.

### `vec3Zero`

!!! info ""
	__Signature__:

	`#!c vec3 vec3Zero()`

	__Description__:

	Returns a `vec3` with the value `vec3(0.0, 0.0, 0.0)`.

## Matrices

### `matrixAdd`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `matrixIdentity`

!!! info ""
	__Signature__:

	`#!c matrix matrixIdentity()`

	__Description__:

	Returns an identity matrix. (a matrix with no transformations applied)

### `matrixInvert`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `matrixLookAt`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `matrixMultiply`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `matrixRotate`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `matrixScale`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `matrixSubtract`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `matrixTranslate`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `matrixTranspose`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

## Input

### `getMouseDelta`

!!! info ""
	__Signature__:

	`#!c vec2 getMouseDelta()`

	__Description__:

	Returns a 2D vector containing the distance the mouse has moved since the last frame.

### `getMouseDrag`

!!! info ""
	__Signature__:

	`#!c vec2 getMouseDrag(int button)`

	__Arguments__:

	- `#!c int button`: The mouse button to check [0-2]
	
	__Description__:

	Returns a 2D vector containing the distance the mouse has been dragged since the given mouse __button__ was pressed.

	__button__ must be one of the following values:

	Constant | Value
	-|-
	`BTN_MOUSE_LEFT` | `0`
	`BTN_MOUSE_RIGHT` | `1`
	`BTN_MOUSE_MIDDLE` | `2`

### `getMouseLock`

!!! info ""
	__Signature__:

	`#!c int getMouseLock()`

	__Description__:

	Returns 1 if the mouse is currently locked. Otherwise, returns 0.

### `getMousePosition`

!!! info ""
	__Signature__:

	`#!c vec2 getMousePosition()`

	__Description__:

	Returns a 2D vector containing the mouse's screen coordinates.

### `getMouseWheel`

!!! info ""
	__Signature__:

	`#!c int getMouseWheel()`

	__Description__:

	Returns 1 if the mouse wheel is being scrolled up.

	Returns -1 if the mouse wheel is being scrolled down.

	Otherwise, returns 0.

### `held`

!!! info ""
	__Signature__:

	`#!c int held(int player, int button)`

	__Arguments__:

	- `#!c int player`: The player to check [0-3]
	- `#!c int button`: The button to check [0-13]
	
	__Description__:

	Returns 1 if the given __player__ is holding the given __button__. Otherwise, returns 0.

	__button__ must be one of the following values:

	Constant | Value
	-|-
	`BTN_UP` | `0`
	`BTN_DOWN` | `1`
	`BTN_LEFT` | `2`
	`BTN_RIGHT` | `3`
	`BTN_TRIANGLE` | `4`
	`BTN_CROSS` | `5`
	`BTN_SQUARE` | `6`
	`BTN_CIRCLE` | `7`
	`BTN_L1` | `8`
	`BTN_L2` | `9`
	`BTN_R1` | `10`
	`BTN_R2` | `11`
	`BTN_SELECT` | `12`
	`BTN_START` | `13`

### `mouseDragging`

!!! info ""
	__Signature__:

	`#!c int mouseDragging(int button)`

	__Arguments__:

	- `#!c int button`: The mouse button to check [0-2]
	
	__Description__:

	Returns 1 if the given mouse __button__ has been held for at least 1 frame, and the mouse has moved since being held.

	Otherwise, returns 0.

	__button__ must be one of the following values:

	Constant | Value
	-|-
	`BTN_MOUSE_LEFT` | `0`
	`BTN_MOUSE_RIGHT` | `1`
	`BTN_MOUSE_MIDDLE` | `2`

### `mouseHeld`

!!! info ""
	__Signature__:

	`#!c int mouseHeld(int button)`

	__Arguments__:

	- `#!c int button`: The mouse button to check [0-2]
	
	__Description__:

	Returns 1 if the given mouse __button__ is being held.

	Otherwise, returns 0.

	__button__ must be one of the following values:

	Constant | Value
	-|-
	`BTN_MOUSE_LEFT` | `0`
	`BTN_MOUSE_RIGHT` | `1`
	`BTN_MOUSE_MIDDLE` | `2`

### `mousePressed`

!!! info ""
	__Signature__:

	`#!c int mousePressed(int button)`

	__Arguments__:

	- `#!c int button`: The mouse button to check [0-2]
	
	__Description__:

	Returns 1 if the given mouse __button__ has been pressed this frame.

	Otherwise, returns 0.

	__button__ must be one of the following values:

	Constant | Value
	-|-
	`BTN_MOUSE_LEFT` | `0`
	`BTN_MOUSE_RIGHT` | `1`
	`BTN_MOUSE_MIDDLE` | `2`

### `mouseReleased`

!!! info ""
	__Signature__:

	`#!c int mouseReleased(int button)`

	__Arguments__:

	- `#!c int button`: The mouse button to check [0-2]
	
	__Description__:

	Returns 1 if the given mouse __button__ has been released this frame.

	Otherwise, returns 0.

	__button__ must be one of the following values:

	Constant | Value
	-|-
	`BTN_MOUSE_LEFT` | `0`
	`BTN_MOUSE_RIGHT` | `1`
	`BTN_MOUSE_MIDDLE` | `2`

### `pressed`

!!! info ""
	__Signature__:

	`#!c int pressed(int player, int button)`

	__Arguments__:

	- `#!c int player`: The player to check [0-3]
	- `#!c int button`: The button to check [0-13]
	
	__Description__:

	Returns 1 if the given __player__ has pressed the given __button__ this frame.

	Otherwise, returns 0.

	__button__ must be one of the following values:

	Constant | Value
	-|-
	`BTN_UP` | `0`
	`BTN_DOWN` | `1`
	`BTN_LEFT` | `2`
	`BTN_RIGHT` | `3`
	`BTN_TRIANGLE` | `4`
	`BTN_CROSS` | `5`
	`BTN_SQUARE` | `6`
	`BTN_CIRCLE` | `7`
	`BTN_L1` | `8`
	`BTN_L2` | `9`
	`BTN_R1` | `10`
	`BTN_R2` | `11`
	`BTN_SELECT` | `12`
	`BTN_START` | `13`

### `released`

!!! info ""
	__Signature__:

	`#!c int released(int player, int button)`

	__Arguments__:

	- `#!c int player`: The player to check [0-3]
	- `#!c int button`: The button to check [0-13]
	
	__Description__:

	Returns 1 if the given __player__ has released the given __button__ this frame.

	Otherwise, returns 0.

	__button__ must be one of the following values:

	Constant | Value
	-|-
	`BTN_UP` | `0`
	`BTN_DOWN` | `1`
	`BTN_LEFT` | `2`
	`BTN_RIGHT` | `3`
	`BTN_TRIANGLE` | `4`
	`BTN_CROSS` | `5`
	`BTN_SQUARE` | `6`
	`BTN_CIRCLE` | `7`
	`BTN_L1` | `8`
	`BTN_L2` | `9`
	`BTN_R1` | `10`
	`BTN_R2` | `11`
	`BTN_SELECT` | `12`
	`BTN_START` | `13`

### `setMouseLock`

!!! info ""
	__Signature__:

	`#!c void setMouseLock(int lock)`

	__Arguments__:

	- `#!c int lock`: Lock setting [true/false]
	
	__Description__:

	If lock is true, hides and locks the mouse to the screen.

	If lock is false, shows and unlocks the mouse.

## Graphics

### `ambientColor`

!!! info ""
	__Signature__:

	`#!c void ambientColor(int color)`

	__Arguments__:

	- `#!c int color`: The ambient light color to use (RGBA32 format)
	
	__Description__:

	Sets the current ambient lighting color.

### `ambientFactor`

!!! info ""
	__Signature__:

	`#!c void ambientFactor(float factor)`

	__Arguments__:

	- `#!c float factor`: Percentage of ambient light tinting [0.0-100.0]
	
	__Description__:

	Sets the current ambient light factor.

	The ambient factor is the percentage of tinting that objects will recieve from ambient lighting.

### `beginMesh`

!!! info ""
	__Signature__:

	`#!c void beginMesh(int primitive)`

	__Arguments__:

	- `#!c int primitive`: The type of mesh primitive to construct [0-2]
	
	__Description__:

	Begins construction of a mesh using the given __primitive__ type.

	__primitive__ must be one of the following values:

	Constant | Value | Description
	-|-|-
	`MESH_LINES` | 0 | Construct line primitives (2 vertices each)
	`MESH_TRIANGLES` | 1 | Construct triangle primitives (3 vertices each)
	`MESH_QUADS` | 2 | Construct quad primitives (4 vertices each)

	Must eventually be followed by a call to [`endMesh()`](#endmesh).

### `blendFactors`

!!! info ""
	__Signature__:

	`#!c void blendFactors(int src, int dest, int eq)`

	__Arguments__:

	- `#!c int src`: The new blending source factor to use [0-14]
	- `#!c int dest`: The new blending destination factor to use [0-14]
	- `#!c int eq`: The new blending equation to use [0-4]
	
	__Description__:

	Changes the current color blending factors and equations for both rgb and alpha.
	
	Must be called before [`blendMode()`](#blendmode).

	Blend mode must be set to `BLEND_CUSTOM` (6) after this call.

	__src__ and __dest__ must be one of the following values:

	Constant | Value
	-|-
	`FACTOR_ZERO` | `0`
	`FACTOR_ONE` | `1`
	`FACTOR_SRC_RGB` | `2`
	`FACTOR_ONE_MINUS_SRC_RGB` | `3`
	`FACTOR_DST_RGB` | `4`
	`FACTOR_ONE_MINUS_DST_RGB` | `5`
	`FACTOR_SRC_ALPHA` | `6`
	`FACTOR_ONE_MINUS_SRC_ALPHA` | `7`
	`FACTOR_DST_ALPHA` | `8`
	`FACTOR_ONE_MINUS_DST_ALPHA` | `9`
	`FACTOR_CONSTANT_RGB` | `10`
	`FACTOR_ONE_MINUS_CONSTANT_RGB` | `11`
	`FACTOR_CONSTANT_ALPHA` | `12`
	`FACTOR_ONE_MINUS_CONSTANT_ALPHA` | `13`
	`FACTOR_SRC_ALPHA_SATURATE` | `14`

	__eq__ must be one of the following values:

	Constant | Value
	-|-
	`EQ_ADD` | `0`
	`EQ_SUBTRACT` | `1`
	`EQ_SUBTRACT_REVERSE` | `2`
	`EQ_MIN` | `3`
	`EQ_MAX` | `4`

### `blendFactorsEx`

!!! info ""
	__Signature__:

	`#!c void blendFactorsEx(int src_rgb, int dest_rgb, int src_alpha, int dest_alpha, int eq_rgb, int eq_alpha)`

	__Arguments__:

	- `#!c int src_rgb`: Blending source rgb factor to use [0-14]
	- `#!c int dest_rgb`: Blending destination rgb factor to use [0-14]
	- `#!c int src_alpha`: Blending source alpha factor to use [0-14]
	- `#!c int dest_alpha`: Blending destination alpha factor to use [0-14]
	- `#!c int eq_rgb`: Blending rgb equation to use [0-4]
	- `#!c int eq_alpha`: Blending alpha equation to use [0-4]

	__Description__:

	Changes the current blending factors and equations for rgb and alpha individually.

	Must be called before [`blendMode()`](#blendmode).

	Blend mode must be set to `BLEND_CUSTOM_EX` (7) after this call.

	See [`blendFactors()`](#blendfactors) for a list of factors and equations.

### `blendMode`

!!! info ""
	__Signature__:

	`#!c void blendMode(int mode)`

	__Arguments__:

	- `#!c int mode`: The new blending mode to use [0-7]
	
	__Description__:

	Changes the current color blending mode setting.	

	__mode__ must be one of the following values:

	Constant | Value
	-|-
	`BLEND_ALPHA` | `0`
	`BLEND_ADD` | `1`
	`BLEND_MULTIPLY` | `2`
	`BLEND_ADD_ALT` | `3`
	`BLEND_SUBTRACT` | `4`
	`BLEND_PREMULTIPLY` | `5`
	`BLEND_CUSTOM` | `6`
	`BLEND_CUSTOM_EX` | `7`

### `camera2D`

!!! info ""
	__Signature__:

	`#!c void camera2D(int camera)`

	__Arguments__:

	- `#!c int camera`: Index of the 2D camera to use [0-3]
	
	__Description__:

	Configures the topmost matrix on the stack to match the view of the given 2D camera.

### `camera3D`

!!! info ""
	__Signature__:

	`#!c void camera3D(int camera)`

	__Arguments__:

	- `#!c int camera`: Index of the 3D camera to use [0-3]
	
	__Description__:

	Configures the topmost matrix on the stack to match the view of the given 3D camera.

	Before the call to draw() each frame, an implicit call to `#!c camera3d(0)` is made.

### `clear`

!!! info ""
	__Signature__:

	`#!c void clear(int flags)`

	__Arguments__:

	- `#!c int flags`: The buffers to clear
	
	__Description__:

	Clears the rendering buffers specified by __flags__.

	__flags__ is a 3-bit bitmask, each bit corresponding to a render buffer.

	The following table lists built-in constants that can be used as __flags__ values:

	Constant | Value | Description
	-|-|-
	`CLEAR_NONE` | Binary: `0b000` (Decimal: `0`) | Do not clear any buffers
	`CLEAR_COLOR` | Binary: `0b100` (Decimal: `4`) | Clear the color buffer (pixel buffer drawn to the screen)
	`CLEAR_DEPTH` | Binary: `0b010` (Decimal: `2`) | Clear the depth buffer (buffer containing each pixel's distance from the camera)
	`CLEAR_STENCIL` | Binary: `0b001` (Decimal: `1`) | Clear the stencil buffer (8-bit buffer used to mask to-be-drawn pixels)
	`CLEAR_ALL` | Binary: `0b111` (Decimal: `7`) | Clear all buffers

	Constants can be bitwise OR'd to clear different combinations of buffers:

	```C
	clear(CLEAR_DEPTH | CLEAR_STENCIL); // clear depth and stencil buffers, but not color
	```

### `clearColor`

!!! info ""
	__Signature__:

	`#!c void clearColor(int color)`

	__Arguments__:

	- `#!c int color`: The new clear color to use. (RGBA32 format)
	
	__Description__:

	Sets the value to fill the color buffer with when [`clear()`](#clear) is called with the `CLEAR_COLOR` flag enabled.

	The default clear color is black. (`0x000000FF`)

### `clearDepth`

!!! info ""
	__Signature__:

	`#!c void clearDepth(float depth)`

	__Arguments__:

	- `#!c float depth`: The new clear depth to use. [0.0-1.0]
	
	__Description__:

	Sets the value to fill the depth buffer with when [`clear()`](#clear) is called with the `CLEAR_DEPTH` flag enabled.

	The default clear depth is 1.0.

### `clearStencil`

!!! info ""
	__Signature__:

	`#!c void clearStencil(int stencil)`

	__Arguments__:

	- `#!c int stencil`: The new clear stencil to use. [0x00-0xFF]
	
	__Description__:

	Sets the value to fill the stencil buffer with when [`clear()`](#clear) is called with the `CLEAR_STENCIL` flag enabled.

	The default clear stencil is `0x00`.

### `colorMask`

!!! info ""
	__Signature__:

	`#!c void colorMask(int flags)`

	__Arguments__:

	- `#!c int flags`: Color channel flags
	
	__Description__:

	Enables/disables writing to the color buffer on a per-channel basis.

	__flags__ is a 4-bit bitmask, each bit corresponding to a color channel.

	The following table lists built-in constants that can be used as __flags__ values:

	Constant | Value | Description
	-|-|-
	`COLOR_NONE` | Binary: `0b0000` (Decimal: `0`) | Disable all writing to the color buffer
	`COLOR_R` | Binary: `0b1000` (Decimal: `8`) | Enable writing the red color channel to the color buffer
	`COLOR_G` | Binary: `0b0100` (Decimal: `4`) | Enable writing the green color channel to the color buffer
	`COLOR_B` | Binary: `0b0010` (Decimal: `2`) | Enable writing the blue color channel to the color buffer
	`COLOR_A` | Binary: `0b0001` (Decimal: `1`) | Enable writing the alpha color channel to the color buffer
	`COLOR_ALL` | Binary: `0b1111` (Decimal: `15`) | Enable all writing to the color buffer

	Constants can be bitwise OR'd to enable different combinations of channels:

	```C
	colorMask(COLOR_R | COLOR_A); // write only to the red and alpha channels of the color buffer
	```

### `cullMode`

!!! info ""
	__Signature__:

	`#!c void cullMode(int mode)`

	__Arguments__:

	- `#!c int mode`: The new face culling mode to use [0-2]`
	
	__Description__:

	Changes the current face culling mode setting.

	__mode__ must be one of the following values:

	Constant | Value | Description
	-|-|-
	`CULL_BACK` | 0 | Cull backfaces
	`CULL_FRONT` | 1 | Cull frontfaces
	`CULL_NONE` | 2 | Disable face culling

### `depthFunc`

!!! info ""
	__Signature__:

	`#!c void depthFunc(int func)`

	__Arguments__:

	- `#!c int func`: The new depth function to use [0-7]
	
	__Description__:

	Sets the function used during depth testing.

	__func__ must be one of the following values:

	Constant | Value | Description
	-|-|-
	`FUNC_LESS` | 0 | Depth test passes if new depth < current depth
	`FUNC_LEQUAL` | 1 | Depth test passes if new depth <= current depth
	`FUNC_GREATER` | 2 | Depth test passes if new depth > current depth
	`FUNC_GEQUAL` | 3 | Depth test passes if new depth >= current depth
	`FUNC_EQUAL` | 4 | Depth test passes if new depth == current depth
	`FUNC_NOTEQUAL` | 5 | Depth test passes if new depth != current depth
	`FUNC_ALWAYS` | 6 | Depth test always passes
	`FUNC_NEVER` | 7 | Depth test never passes

### `depthMask`

!!! info ""
	__Signature__:

	`#!c void depthMask(int enable)`

	__Arguments__:

	- `#!c int enable`: Depth buffer writing flag [true/false]
	
	__Description__:

	Enables/disables writing to the depth buffer.

### `depthTest`

!!! info ""
	__Signature__:

	`#!c void depthTest(int enable)`

	__Arguments__:

	- `#!c int enable`: Depth testing flag [true/false]
	
	__Description__:

	Enables/disables depth testing.

### `drawObj`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `drawObjEx`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `endMesh`

!!! info ""
	__Signature__:

	`#!c void endMesh()`

	__Description__:

	Finalizes the construction of a mesh.

	Must only be called after a matching call to [`beginMesh()`](#beginmesh).

### `fogColor`

!!! info ""
	__Signature__:

	`#!c void fogColor(int color)`

	__Arguments__:

	- `#!c int color: the fog color to use (RGBA32 format)`
	
	__Description__:

	Sets the current fog tint color.

	

	See fogmode().

### `fogEnd`

!!! info ""
	__Signature__:

	`#!c void fogEnd(float end);`

	__Arguments__:

	- `#!c float end: the distance from the camera where the`
	- `#!c fog ends. [0.0-1000.0]`
	
	__Description__:

	Sets the fog end distance setting.

	

	See fogmode().

### `fogMode`

!!! info ""
	__Signature__:

	`#!c void fogMode(int mode)`

	__Arguments__:

	- `#!c int mode: the fog mode to use [true/false]`
	
	__Description__:

	Enables/disables fog.

	

	If mode is true, fog rendering will be enabled.

	Otherwise, fog rendering will be disabled.

	

	Fog is rendered by fading the color of geometry to the set fog color.

	The fog start setting determines how far from the camera the fade begins.

	The fog end setting is the distance from the camera where objects

	Will be fully tinted to the fog color.

### `fogStart`

!!! info ""
	__Signature__:

	`#!c void fogStart(float start);`

	__Arguments__:

	- `#!c float start: the distance from the camera to start`
	- `#!c rendering fog. [0.0-1000.0]`
	
	__Description__:

	Sets the fog starting distance setting.

	

	See fogmode().

### `frustum`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `getCam2D`

!!! info ""
	__Signature__:

	`#!c cam2d* getCam2D(int camera)`

	__Arguments__:

	- `#!c int camera: index of the 2D camera to get [0-3]`
	
	__Description__:

	Returns a pointer to the given 2d camera.

### `getCam3D`

!!! info ""
	__Signature__:

	`#!c cam3d* getCam3D(int camera)`

	__Arguments__:

	- `#!c int camera: index of the 3D camera to get [0-3]`
	
	__Description__:

	Returns a pointer to the given 3d camera.

### `getLight`

!!! info ""
	__Signature__:

	`#!c light* getLight(int light)`

	__Arguments__:

	- `#!c int light: index of the light to get [0-7]`
	
	__Description__:

	Returns a pointer to the given light.

### `getModelViewMatrix`

!!! info ""
	__Signature__:

	`#!c matrix getModelViewMatrix()`

	__Description__:

	Returns a copy of the topmost model-view matrix.

### `getProjectionMatrix`

!!! info ""
	__Signature__:

	`#!c matrix getProjectionMatrix()`

	__Description__:

	Returns a copy of the topmost projection matrix.

### `getTopMatrix`

!!! info ""
	__Signature__:

	`#!c matrix getTopMatrix()`

	__Description__:

	Returns a copy of the topmost matrix of the current matrix stack.

### `identity`

!!! info ""
	__Signature__:

	`#!c void identity()`

	__Description__:

	Resets the topmost matrix of the current matrix stack to an identity matrix.

	(a matrix with no transformations applied)

### `lightingMode`

!!! info ""
	__Signature__:

	`#!c void lightingMode(int mode)`

	__Arguments__:

	- `#!c int mode: the lighting mode to use [true/false]`
	
	__Description__:

	Enables/disables vertex lighting.

	

	If mode is true, lighting will be enabled.

	Otherwise, lighting will be disabled.

	

	Vertex lighting changes vertex colors to simulate lighting.

	When lighting is enabled, meshcolor() calls will be ignored.

	

	Ambient lighting is also calculated when lighting is enabled.

	Ambient lighting is a form of light that every object

	Recieves equally.

### `lookAt`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `meshColor`

!!! info ""
	__Signature__:

	`#!c void meshColor(int color)`

	__Arguments__:

	- `#!c int color: the color to use for the current vertex (RGBA32 format)`
	
	__Description__:

	Submits the tint color for the current mesh vertex.

	

	Vertex colors can be used to tint the texture of a mesh.

	The colors of each vertex are blended across the mesh surface.

	

	Vertex colors are multiplied with texture pixel colors,

	So a vertex color of pure white will result in the

	Original pixel color.

	

	If lighting is enabled, this function does nothing.

### `meshNormal`

!!! info ""
	__Signature__:

	`#!c void meshNormal(vec3 normal)`

	__Arguments__:

	- `#!c vec3 normal: the 3D normal vector to use for the current vertex`
	
	__Description__:

	Submits the 3d normal vector for the current mesh vertex.

	The vector must be normalized. (normal must have a length of 1)

	

	Normal vectors are used when calculating lighting.

	A vertex with a normal vector pointing toward a light will recieve more

	Light than one with a normal vector pointing away from the light.

	

	If lighting is not enabled, this function does nothing.

### `meshUV`

!!! info ""
	__Signature__:

	`#!c void meshUV(vec2 uv)`

	__Arguments__:

	- `#!c vec2 uv: the 2D texture coordinates to use for the current vertex`
	
	__Description__:

	Submits the 2d texture coordinates for the current mesh vertex.

	

	(0.0, 0.0) corresponds to the top-left corner of the texture.

	(1.0, 1.0) corresponds to the bottom-right corner of the texture.

	

	The normal range for uv coordinates is (0.0, 0.0) to (1.0, 1.0),

	Values outside the 0.0-1.0 range will be treated differently

	Depending on the current texture mode. (see settexturemode())

### `meshVertex`

!!! info ""
	__Signature__:

	`#!c void meshVertex(vec3 v)`

	__Arguments__:

	- `#!c vec3 v: the 3D coordinates to use for the current vertex`
	
	__Description__:

	Submits the 3d coordinates for the current mesh vertex and

	Finalizes the vertex.

	

	This function should be called after all other desired vertex properties

	(uv, color, normal) have been submitted.

### `meshVertex2D`

!!! info ""
	__Signature__:

	`#!c void meshVertex2D(vec2 v)`

	__Arguments__:

	- `#!c vec2 v: the 2D screen coordinates to use for the current vertex`
	
	__Description__:

	Submits the 2d coordinates for the current mesh vertex and

	Finalizes the vertex.

	

	This function should be called after all other desired vertex properties

	(uv, color, normal) have been submitted.

### `multiplyTopMatrix`

!!! info ""
	__Signature__:

	`#!c void multiplyTopMatrix(matrix m)`

	__Arguments__:

	- `#!c matrix m: the matrix to multiply by`
	
	__Description__:

	Multiplies the topmost matrix of the current stack by the given matrix.

### `ortho`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `polygonMode`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `popMatrix`

!!! info ""
	__Signature__:

	`#!c void popMatrix()`

	__Description__:

	Pops the topmost matrix off of the current matrix stack.

### `print2D`

!!! info ""
	__Signature__:

	`#!c void print2D(int x, int y, int color, string fmt, ...)`

	__Arguments__:

	- `#!c int x     : text screen x position`
	- `#!c int y     : text screen y position`
	- `#!c int color : the text color to use (RGBA32 format)`
	- `#!c string fmt: format text string`
	- `#!c ...       : format values`
	
	__Description__:

	Prints a formatted text string to the screen.

	

	Format specifiers:

	%%       literal '%' character

	%d or %i signed integer value

	%u       unsigned integer value

	%f       float value

	%x       lowercase hexidecimal integer value

	%x       uppercase hexidecimal integer value

	%v2      vec2 value

	%v3      vec3 value

### `pushMatrix`

!!! info ""
	__Signature__:

	`#!c void pushMatrix()`

	__Description__:

	Pushes a copy of the current matrix to the top of the current matrix stack.

### `rotate`

!!! info ""
	__Signature__:

	`#!c void rotate(vec3 v)`

	__Arguments__:

	- `#!c vec3 v: the vector to rotate by`
	
	__Description__:

	Rotates the topmost matrix of the current matrix by the 3d vector v.

	Rotation angles must be in degrees.

### `scale`

!!! info ""
	__Signature__:

	`#!c void scale(vec3 v)`

	__Arguments__:

	- `#!c vec3 v: the vector to scale by`
	
	__Description__:

	Scales the topmost matrix of the current matrix by the 3d vector v.

### `scissor`

!!! info ""
	__Signature__:

	`#!c void scissor(int x, int y, int width, int height)`

	__Arguments__:

	- `#!c int x`: Scissor screen x position [0-479]
	- `#!c int y`: Scissor screen y position [0-359]
	- `#!c int width`: Scissor width [1-480]
	- `#!c int height`: Scissor height [1-360]
	
	__Description__:
	
	Restricts all rendering to the rectangle defined by __x__, __y__, __width__, and __height__.

	Pixels outside of the rectangle will not be affected by any drawing commands.

### `scissorMode`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `setModelViewMatrix`

!!! info ""
	__Signature__:

	`#!c void setModelViewMatrix(matrix m)`

	__Arguments__:

	- `#!c matrix m: the matrix to use`
	
	__Description__:

	Sets the topmost model-view matrix to the given matrix.

### `setProjectionMatrix`

!!! info ""
	__Signature__:

	`#!c void setProjectionMatrix(matrix m)`

	__Arguments__:

	- `#!c matrix m: the matrix to use`
	
	__Description__:

	Sets the topmost projection matrix to the given matrix.

### `sprite2D`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `sprite2DEx`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `stencilFunc`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `stencilMask`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `stencilMode`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `stencilOp`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `texture`

!!! info ""
	__Signature__:

	`#!c void texture(int x, int y, int width, int height)`

	__Arguments__:

	- `#!c int x     : texture window x position [0-1023]`
	- `#!c int y     : texture window y position [0-1023]`
	- `#!c int width : texture window width [1-256]`
	- `#!c int height: texture window height [1-256]`
	
	__Description__:

	Changes the window of texture memory to use as the current texture.

	

	A maximum texture size of 256x256 can be specified.

	

	Texture uv coordinates will be mapped to the specified texture window.

### `textureMode`

!!! info ""
	__Signature__:

	`#!c void textureMode(int mode)`

	__Arguments__:

	- `#!c int mode: the new texture mode to use [0-2]`
	
	__Description__:

	Changes the current texture mode setting.

	

	Mode must be one of the following values:

	0: repeat texture (default)

	1: clamp texture to edges

	2: disable texturing

	

	Modes 0 and 1 determine whether uvs outside of the 0.0-1.0 range

	Will cause the texture to be repeated accross a surface, or

	If uvs should be clamped to the 0.0-1.0 range.

	

	Mode 2 will ignore texture pixel colors and output

	Pure white instead. useful when used with vertex colors.

### `translate`

!!! info ""
	__Signature__:

	`#!c void translate(vec3 v)`

	__Arguments__:

	- `#!c vec3 v: the vector to translate by`
	
	__Description__:

	Translates the topmost matrix of the current matrix by the 3d vector v.

### `viewport`

!!! info ""
	__Signature__:

	`#!c void viewport(int x, int y, int width, int height)`

	__Arguments__:

	- `#!c int x`: Viewport screen x position [0-479]
	- `#!c int y`: Viewport screen y position [0-359]
	- `#!c int width`: Viewport width [1-480]
	- `#!c int height`: Viewport height [1-360]
	
	__Description__:
	
	Defines the tranformation of coordinates of pixels to render into screen coordinates.

	By default, pixels are rendered at 1:1 screen coordinates, but this function allows rendering output to be scaled to the rectangle defined by __x__, __y__, __width__, and __height__.

## Audio

### `getTrackBPM`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `getTrackPan`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `getTrackVolume`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `muteTrack`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `muteTracks`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `pauseTrack`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `pauseTracks`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `playPattern`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `playSong`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `playTrack`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `playWav`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `playWavEx`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `resumeTrack`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `resumeTracks`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `setTrackBPM`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `setTrackPan`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `setTrackVolume`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `stopTrack`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `stopTracks`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `unmuteTrack`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `unmuteTracks`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

## Physics

### `checkCollision`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `getRaycastNormal`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `getRaycastPoint`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

### `raycast`

!!! info ""
	__Signature__:

	`#!c ...`

	__Arguments__:

	- `#!c ...`
	
	__Description__:

	...

## Memory

### `initMemCard`

!!! info ""
	__Signature__:

	`#!c void initMemCard(string id)`

	__Arguments__:

	- `#!c string id: unique identifier for memory card data`
	
	__Description__:

	Initializes the system's memory card memory range.

	Memory card data is stored in the address range 0x05800000 to 0x05800fff.

	

	Id is a string used to identify saved memory card data.

	Id must be between 1 and 16 characters long and may only contain

	The characters a-z, a-z, 0-9, and _

	

	If save data matching the given id exists, it will be loaded.

	Write bytes to the address range 0x05800000 to 0x05800fff to save

	Data to the memory card.

### `loadObjBank`

!!! info ""
	__Signature__:

	`#!c void loadObjBank(int bank)`

	__Arguments__:

	- `#!c int bank: index of the object bank to load [0-3]`
	
	__Description__:

	Loads an object bank from the cartridge into system memory.

	

	System object data is stored in the address range

	0x00c00000 to 0x00f5ffff.

### `loadSeqBank`

!!! info ""
	__Signature__:

	`#!c void loadSeqBank(int bank)`

	__Arguments__:

	- `#!c int bank: index of the sequencer bank to load [0-7]`
	
	__Description__:

	Loads a sequencer bank from the cartridge into system memory.

	

	System sequencer data is stored in the address range

	0x01700000 to 0x0173ffff.

### `loadTexBank`

!!! info ""
	__Signature__:

	`#!c void loadTexBank(int bank)`

	__Arguments__:

	- `#!c int bank: index of the texture bank to load [0-3]`
	
	__Description__:

	Loads a texture bank from the cartridge into system memory.

	

	System texture data is stored in the address range

	0x00800000 to 0x00bfffff.

### `loadWavBank`

!!! info ""
	__Signature__:

	`#!c void loadWavBank(int bank)`

	__Arguments__:

	- `#!c int bank: index of the wave bank to load [0-1]`
	
	__Description__:

	Loads a wave bank from the cartridge into system memory.

	

	System wave data is stored in the address range

	0x01000000 to 0x016fffff.

### `memcpy`

!!! info ""
	__Signature__:

	`#!c void memcpy(void* destination, void* source, int n)`

	__Arguments__:

	- `#!c void* destination: the memory address to write to`
	- `#!c void* source     : the memory address to read from`
	- `#!c int n            : the amount of bytes to read`
	
	__Description__:

	Copies n bytes from source to destination.

	

	Source and destination buffers may safely overlap.

### `memset`

!!! info ""
	__Signature__:

	`#!c void memset(void* destination, int n, int value)`

	__Arguments__:

	- `#!c void* destination: the memory address to write to`
	- `#!c int n            : the amount of bytes to write`
	- `#!c int value        : byte value to write`
	
	__Description__:

	Copies the given byte value to the first n bytes

	Starting at the destination address.

### `peek8`

!!! info ""
	__Signature__:

	`#!c int peek8(void* address)`

	__Arguments__:

	- `#!c void* address: memory pointer to read from`
	
	__Description__:

	Returns the value of the byte at the given memory address.

### `peek32`

!!! info ""
	__Signature__:

	`#!c int peek32(void* address)`

	__Arguments__:

	- `#!c void* address: memory pointer to read from`
	
	__Description__:

	Returns the 32-bit integer value starting at the given memory address.

### `poke8`

!!! info ""
	__Signature__:

	`#!c void poke8(void* address, int value)`

	__Arguments__:

	- `#!c void* address: memory pointer to write to`
	- `#!c int value    : byte value to write`
	
	__Description__:

	Writes the given byte to the given memory address.

### `poke32`

!!! info ""
	__Signature__:

	`#!c void poke32(void* address, int value)`

	__Arguments__:

	- `#!c void* address: memory pointer to write to`
	- `#!c int value    : 32-bit integer value to write`
	
	__Description__:

	Writes the 32-bit integer to the given memory address.

## Misc

### `time`

!!! info ""
	__Signature__:

	`#!c float time()`

	__Description__:

	Returns the number of seconds that the current cart has been running.

### `vargc`

!!! info ""
	__Signature__:

	`#!c int vargc()`

	__Description__:

	Returns the remaining number of vararg bytes for a vararg function.

	

	Must only be called from a vararg function.

### `vargv`

!!! info ""
	__Signature__:

	`#!c void* vargv(int offset)`

	__Arguments__:

	- `#!c int offset: the number of bytes to advance the vararg pointer`
	
	__Description__:

	Returns a pointer to the current vararg argument and advances the

	Vararg pointer by $offset bytes.

	

	Must only be called from a vararg function.
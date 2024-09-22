# Building

## Introduction

To build ERA-3D from source, you must first [install CMake](https://cmake.org/download/).

After CMake is installed, follow the instructions for your operating system.

## Building on Windows

### Configuring w64DevKit

To configure a building environment, it is recommended to [install w64DevKit](https://github.com/skeeto/w64devkit/releases).

Run `...\w64devkit\w64devkit.exe` to launch a shell environment for compiling C programs. All commands listed in the following instructions assume you are running `w64devkit.exe`.

### Installing Nelua

Download the [latest Nelua release](https://github.com/edubart/nelua-lang/releases) and extract the files to a suitable install location.

Add the path containing `nelua.exe` to the `Path` environment variable.

### Installing Raylib

Download the [Raylib 5.0 mingw-w64 release](https://github.com/raysan5/raylib/releases/tag/5.0) and extract the files from the zip archive.

Copy all the `.h` files from the `include` folder into `...\w64devkit\x86_64-w64-mingw32\include`.

Copy `libraylib.a` from the `lib` folder into `...\w64devkit\x86_64-w64-mingw32\lib`.

### Building and Installing E3DBlipKit

Clone the [E3DBlipKit repository](https://github.com/AuzFox/E3DBlipKit) or download and extract everything from the source zip.

Enter the `E3DBlipKit` folder using the `w64DevKit` shell and run the following commands:

```sh
mkdir build
cd build
cmake -G "MinGW Makefiles" ..
make
```

If E3DBlipKit built successfully, you will find `libblipkit.a` in `E3DBlipKit\build\src`. Copy `libblipkit.a` into `...\w64devkit\x86_64-w64-mingw32\lib`.

Copy all the `.h` files from the `E3DBlipKit\src` folder into `...\w64devkit\x86_64-w64-mingw32\include\blipkit`. (Create the `blipkit` folder inside `include`)

### Building ERA-3D

If all of the above steps have been completed, it's time to finally build ERA-3D!

Clone the [ERA-3D repository](https://github.com/AuzFox/ERA-3D) or download and extract everything from the source zip.

Enter the `ERA-3D` folder using the `w64DevKit` shell and run the following command:

```sh
nelua --release --cflags="-static" src/main.nelua -o era-3d
```

If the build succeeded, you should now have `era-3d.exe` in the `ERA-3D` folder.

Copy `era-3d.exe` and the `ERA-3D\assets` folder into your desired install location.

## Building on Linux

### Installing Nelua

Follow the linux instructions for [installing Nelua](https://nelua.io/installing/).

### Installing Raylib

Download the [Raylib 5.0 linux release](https://github.com/raysan5/raylib/releases/tag/5.0) and extract the files from the zip archive.

Copy all the `.h` files from the `include/` folder into `/usr/local/include/`.

Copy `libraylib.a` from the `lib/` folder into `/usr/local/lib/`.

### Building and Installing E3DBlipKit

Clone the [E3DBlipKit repository](https://github.com/AuzFox/E3DBlipKit) or download and extract everything from the source zip.

Enter the `E3DBlipKit` folder and run the following commands:

```sh
mkdir build
cd build
cmake ..
make
```

If E3DBlipKit built successfully, you will find `libblipkit.a` in `E3DBlipKit/build/src/`. Copy `libblipkit.a` into `/usr/local/lib`.

Copy all the `.h` files from the `E3DBlipKit/src` folder into `/usr/local/include/blipkit`. (Create the `blipkit` folder inside `include/`)

### Building ERA-3D

If all of the above steps have been completed, it's time to finally build ERA-3D!

Clone the [ERA-3D repository](https://github.com/AuzFox/ERA-3D) or download and extract everything from the source zip.

Enter the `ERA-3D/` directory and run the following command:

```sh
nelua --release --cflags="-static" src/main.nelua -o era-3d
```

If the build succeeded, you should now have the `era-3d` executable in the `ERA-3D/` folder.

Copy `era-3d` and the `ERA-3D/assets/` folder into your desired install location.
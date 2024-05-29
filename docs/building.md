# Building

To build ERA-3D, you must first [install Nelua](https://nelua.io/installing/).
Follow the installation instructions on the Nelua website.

Once Nelua is installed, build and install the following C libraries:

- [raylib v5.0](https://github.com/raysan5/raylib)
- [BlipKit](https://github.com/detomon/BlipKit)
- [zip](https://github.com/kuba--/zip)

Once all dependencies are installed, clone this repository and run the following commands:

```
cd .../ERA-3D/
nelua --release src/main.nelua -o era-3d
```

You should now have the `era-3d` executable.
move `era-3d` and the `assets` directory to the desired install location.

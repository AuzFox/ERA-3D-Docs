# User Guide

## Introduction

!!! warning
    The asset editors built into ERA-3D are still in early development, and are missing important functionality.

    It is currently recommended to use external editors for creating assets like textures and 3D models.

## General Controls

The following keyboard shortcuts are always available, except while an asset import dialog or the console is open:

- ++ctrl+left++ / ++right++: Switch editors
- ++ctrl+r++: Run cart
- ++ctrl+enter++: Open/close console
- ++ctrl+o++: Load cart file
- ++ctrl+s++: Save cart
- ++ctrl+shift+s++: Save cart as

## Editor Screens

TODO

### Code Editor

This screen is where the ERA-C code for the current cart is written.

#### Code Editor Controls

- ++left++ / ++right++ / ++up++ / ++down++: Move cursor
- ++home++: Move cursor to the beginning of the line
- ++end++: Move cursor to the end of the line
- ++page-up++: Move cursor up several lines
- ++page-down++: Move cursor down several lines
- ++alt+up++: Move line up
- ++alt+down++: Move line down
- ++ctrl+d++: Duplicate line
- ++shift+tab++: Deindent line
- ++ctrl+i++: Import code text file (current code is replaced!)

### Audio Sequencer (Tracker)

!!! warning
    Many important features of the Tracker have not been implemented yet.

The Audio Sequencer allows audio samples stored on the cartridge to be sequenced and played back by the soundchip.

#### General Tracker Controls

- ++left++ / ++right++ / ++up++ / ++down++: Move cursor
- ++tab++: Move cursor to next track
- ++shift+tab++: Move cursor to previous track
- ++alt+up++ / ++down++: Switch views
- ++space++: Play/stop song
- ++ctrl+i++ Import an audio file (`.wav`) into the selected [WAVBANK](memory-map.md#wavbanks)

#### Song View Controls

- ++0++-++9++, ++a++-++f++: Change pattern hex value

#### Pattern View Controls

TODO

#### Instrument View Controls

TODO

### Model Editor

!!! warning
    The Model Editor has not been implemented yet.

    However, on the Model Editor screen, you can press ++ctrl+i++ to import a 3D model file (`.obj`, `.gltf/glb`) into [OBJBANK 0](memory-map.md#objbanks).

TODO

### Texture Editor

TODO

#### Texture Editor Controls

- ++ctrl+i++ Import an image file (`.png`) into the selected [TEXBANK](memory-map.md#texbanks) (the image being imported MUST be 1024x1024!)

### Console

The console allows the user to run commands to configure ERA-3D's settings, as well as view API documentation.

!!! warning
    The API documentation accessed using the console is not up-to-date with the online version.

    For now, it is recommended to use the [API Reference page](api-reference.md) instead.

#### Console Controls

- ++enter++: Run command`

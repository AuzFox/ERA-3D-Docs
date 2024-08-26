# Configuration

## Introduction

ERA-3D stores configuration data, carts, and memory card data in its own folders on the filesystem.

## Data Directories

The ERA-3D data directory can be found in the following places:

=== "Windows"

	```
	C:\Users\username\AppData\Roaming\era-3d
	```

=== "Linux"

	```
	~/.era-3d
	```

Inside the `era-3d` directory are the following items:

- `carts` directory: default location of saved cart files
- `memcards` directory: used for storing memcard data files
- `config.json`: ERA-3D configuration file

## Config File Settings

The following table lists all available configuration settings for `config.json`.

Setting | Accepted Values | Default Value | Description
-|-|-|-
`log_level` | 0-7 | 7 | Raylib event log filter level (see Log Levels table below)
`vsync` | `true`/`false` | `true` | VSYNC enable flag
`highdpi` | `true`/`false` | `true` | HIGHDPI enable flag
`draw_fps` | `true`/`false` | `false` | Debug FPS counter display flag
`crt_blur` | `true`/`false` | `true` | CRT blur effect flag
`crt_noise` | `true`/`false` | `true` | CRT static/noise effect flag
`crt_scanlines` | `true`/`false` | `true` | CRT scanline effect flag

The following table lists the possible values for the `log_level` setting.

Levels are ranked, with each level filtering out all events of lower level value.

Log Level | Description
-|-
0 | Log all events
1 | Log trace events and higher
2 | Log debug events and higher
3 | Log info events and higher
4 | Log warning events and higher
5 | Log error events and higher
6 | Log fatal error events
7 | Disable event logging

# coderun
Bash script to easily compile and run files. Currently supports C/C++ and Java with more coming soon.

# Installation
Simply clone the repository, and optionally add it to PATH

# Documentation

## Usage
`coderun FILE [OPTIONS]`

## Parameters
| Parameters | Description |
| ---------- | ----------- |
| `-e`, `--file-extension` | Specified extension of the file. This is optional |
| `-c`, `--compiler-flags` | Accepts a string that will be passed to the compiler |
| `-a`, `--args` | Accepts a string that will be passed to the program as arguments |
| `-C`, `--config` | Used to specify a config file containing predefined compiler flags and arguments. `FILENOEXTENSION` may be used to represent the filename without extension |
| `-m`, `--mode` | Used to specify the mode |
| `-h`, `--help` | Displays help |

**Note:** Values from `-C/--config` are overriden by any compiler flags or arguments passed

## Config Files
By default, the script checks `$HOME/.coderun.cfg`. 
#### Format
```
[FILETYPE]
compiler-flags=val1
args=val2

[FILETYPE:MODE]
compiler-flags=val3
args=val4

...
```

Mode is an optional parameter used to facilitate the creation of multiple configurations for the same filetype. If no mode is specified, configs under `[FILETYPE]` are read

# Example
#### coderun.cfg
```
[CPP]
compiler-flags=-o FILENOEXTENSION
args=

[CPP:strict]
compiler-flags=-o FILENOEXTENSION -Wall -Werror -Wextra -O2
args=
```
#### Without parameters:
`coderun hello_world.cpp`

#### With parameters
`coderun -c "-o hello_world" hello_world.cpp`

#### With a config file
`coderun -C coderun.cfg hello_world.cpp`

#### With mode
`coderun -m strict hello_world.cpp`

# License
coderun is released under Apache 2.0 License

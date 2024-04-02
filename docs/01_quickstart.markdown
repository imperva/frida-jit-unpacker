---
layout: page
title: Quick Start
order: 1
permalink: /quickstart/

---

## Quick Start

# Requirements :
The software runs in Windows > 10 environment with x86_64 architecture 

# Installation
- Download the archive release_1.0_x64.zip from the release section and extract it anywhere in your environment.

# Usage
- Create a directory called `executables` and add your sample and its dependencies to it. 
- Run the following command from the release folder:
```shell
> dist/x64/fjp.exe [OPTIONS] -f <input_file_path> -o <output_file_path>
```

# Options
The list of options and the information regarding their usage can be obtained via the `--help` option :
```txt
> dist/x64/fjp.exe --help

______      _      _            ___  _  _                  ______             _
|  ___|    (_)    | |          |_  |(_)| |                 | ___ \           | |
| |_  _ __  _   __| |  __ _      | | _ | |_   _   _  _ __  | |_/ /__ _   ___ | | __ ___  _ __
|  _|| '__|| | / _` | / _` |     | || || __| | | | || '_ \ |  __// _` | / __|| |/ // _ \| '__|
| |  | |   | || (_| || (_| | /\__/ /| || |_  | |_| || | | || |  | (_| || (__ |   <|  __/| |
\_|  |_|   |_| \__,_| \__,_| \____/ |_| \__|  \__,_||_| |_|\_|   \__,_| \___||_|\_\___||_|
 
 
 
usage: fjp [-h] -f EXECUTABLE [-t TIMEOUT] [-o OUTPUT] [-r] [-sr SCANNING_RANGE] [-s COMPILE_FUNCTION] [-l]
 
Tool to recover the original IL code of running methods from a packed .NET
assembly.
 
optional arguments:
  -h, --help            show this help message and exit
  -f EXECUTABLE, --file EXECUTABLE
                        Path of the sample
  -t TIMEOUT, --timeout TIMEOUT
                        Execution timeout
  -o OUTPUT, --output OUTPUT
                        Output file path
  -r, --resolve_token   Recover encrypted tokens
  -sr SCANNING_RANGE, --scanning_range SCANNING_RANGE
                        Number of assembly instructions to scan to find hook address (0
                        - 15).
  -s COMPILE_FUNCTION, --compile_function COMPILE_FUNCTION
                        Either compileMethod, jitNativeCode or
                        compCompileHelper for now
```

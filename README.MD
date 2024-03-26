
![Frida Jit Unpacker Logo](images/logo.png)

# Frida-Jit-unPacker

## Description
The Frida-Jit-unPacker aims at supporting researchers and analysts in their attempts to understand the behavior of malicious software in order to provide a mitigation. 
This tool uses the [Frida instrumentation toolkit](https://frida.re/) to inject scripts into [the CLR](https://en.wikipedia.org/wiki/Common_Language_Runtime) and manipulate the behavior of the .NET executable to retrieve the original code.
More precisely, this tool intercepts the communication between the CLR components in order retrieve the original IL code of a packed assembly.

If you liked this software, please, add a GitHub star ⭐️, thank you !

### Assumption
We assume here that the packer saves encrypted the orginal IL code of the application and overwrites the method information in the assembly. Then, whenever compilation of a specific method occurs, the packer intercepts the relevant APIs (CompileMethod, ResolveToken ...) in order to provide the original information, just in time, and replaces the fake data.

### Principle
The unpacker uses Frida to place hooks to intercept the same components of the CLR (Method compilation, Token resolution, ...) but at a lower level than the packer. Moreover, it uses a stealthy approach by placing hooks not at the start or end of functions for example, but uses a smart hooking strategy to evade potential detection by the packer. 

## Requirements :
The software runs in Windows > 10 environment with x86_64 architecture 

## Installation
- Download the archive release_1.0_x64.zip from the release section and extract it anywhere in your environment.

## Usage
- Create a directory called `executables` and add your sample and its dependencies to it. 
- Run the following command from the release folder:
```shell
> dist/x64/fjp.exe [OPTIONS] -f <input_file_path> -o <output_file_path>
```

### Options
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
 

## Disclaimer:
This tool shouldn't be used for any illegal activity.

## Warning
1. Frida is often flagged wrongly by anti-viruses. 
2. It's obviously recommended to run any analysis in a dedicated VM for malware analysis. 


## Contributions
Become part of our community and engage with us on any topic through GitHub Discussions. 
Should you encounter difficulties with Frida-Jit-unPacker or wish to provide feedback, feel free to open an issue. Additional details can be found in our contribution documentation.

## More about Imperva

Frida-Jit-unPacker is an [Imperva](https://imperva.com) project.  
Imperva is a cybersecurity leader whose mission is to protect data and all paths to it. 
Look [here](https://www.imperva.com/) to see Imperva products.

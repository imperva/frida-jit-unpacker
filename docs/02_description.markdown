---
layout: page
title: Description
permalink: /description/
order: 2
redirect_from:
  - /
---

## Frida-Jit-unPacker

# General Description
The Frida-Jit-unPacker aims at helping researchers and analysts understand the behavior of malicious .NET packed samples in order to provide a mitigation. 
This tool uses the [Frida instrumentation toolkit](https://frida.re/) to inject scripts into [the CLR](https://en.wikipedia.org/wiki/Common_Language_Runtime) and manipulate the behavior of the .NET executable to retrieve the original code.
More precisely, this tool intercepts the communication between the CLR components in order retrieve the original IL code of a packed assembly.

If you liked this software, please, add a GitHub star ⭐️, thank you !

# Assumption
We assume here that the packer saves encrypted the orginal IL code of the application and overwrites the method information in the assembly. Then, whenever compilation of a specific method occurs, the packer intercepts the relevant APIs (CompileMethod, ResolveToken ...) in order to provide the original information, just in time, and replaces the fake data.

# Principle
The unpacker runs the sample and uses Frida to place hooks and intercept the components of the CLR (Method compilation, Token resolution, ...), at a lower level than the packer. Moreover, it uses a stealthy approach by placing hooks not at the start or end of functions for example, but uses a smart hooking strategy to evade potential detection by the packer. 

# Smart Hooking Strategy
The program uses Frida to disassemble CLR functions and place hooks as far as possible from packer monitoring points (start address of the function for example) while still collecting their input.
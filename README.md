# Quick OpenGL Loader (QOGLL)

Quick, minimal, single header OpenGL function loader with zero-dependencies for C/C++ projects.

So far the focus is to get OpenGL 3.3 core up and running on Windows. Loading other versions of OpenGL and suport for other platforms is on the todo list though.

## Features
Single header + optional implementation (.h/.c)
No dependencies, small footprint, simple API.
Optional GetProcAddress implementation included (only windows is supported so far which uses wglGetProcAddress and fallbacks to opengl32.dll for core functions).

## TODOs
Support more functions up to OpenGL 4.x and common extensions.
Support Linux: use glXGetProcAddressARB.
Support macOS: use dlsym on OpenGL framework or NSGL entrypoints.
Optional GLES2/GLES3 mode.
Bring back GL_CHECK wrapper for all funcs.
Define enums and useful types for all GLenums instead of just macros.
Lazy resolution of OpenGL function pointers at first call?
Maybe switch to a more permissive license?

Provide compile-time defines for features (implement those features):
QGL_NO_ENUMERATIONS
QGL_NO_INLINE_WRAPPERS
QGL_DISABLE_EXTENSIONS
QGL_GLES (for GLES builds)

## Usage
1. Add qogll.h to your project.
2. In one .c/.cpp file define QOGLL_IMPLEMENTATION before including it:
```c
#define QOGLL_IMPLEMENTATION
#include"qogll.h"
```
3. Load OpenGL functions by calling `QGL_init()` (after creating an OpenGL context).
```c
//Create OpenGL context first
QGL_init(QGL_get_proc_address); //or pass your own GetProcAddress
//Use available gl functions
```


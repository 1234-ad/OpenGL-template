# Submodule Migration Guide

## Overview
This PR migrates STB and FileWatcher from direct file inclusion to Git submodules for better dependency management and version control.

## Changes Made

### 1. Added Git Submodules
- **STB**: Added as submodule from `https://github.com/nothings/stb.git`
- **FileWatcher**: Added as submodule from `https://github.com/ThomasMonkman/filewatch.git`

### 2. Updated Build Configuration
- Modified `CMakeLists.txt` to include submodule paths
- Updated include directories to reference submodule locations

## Migration Steps for Existing Users

If you have an existing clone of this repository, follow these steps:

### 1. Remove Old Files
```bash
# Remove the old standalone files
rm external/FileWatch.hpp
rm src/stb_image.h
```

### 2. Initialize Submodules
```bash
# Update .gitmodules
git pull origin main

# Initialize and update all submodules
git submodule update --init --recursive
```

### 3. Verify Installation
After initialization, you should have:
- `external/stb/` directory with STB headers
- `external/filewatch/` directory with FileWatch headers

### 4. Update Include Paths (if needed)
The CMakeLists.txt has been updated to include the new paths. If you have custom build scripts, update them to reference:
- `external/stb/` for STB headers
- `external/filewatch/` for FileWatch headers

## For New Users

Simply clone with submodules:
```bash
git clone --recursive https://github.com/CGS-IITKGP/OpenGL-template.git
```

Or if already cloned:
```bash
git submodule update --init --recursive
```

## Benefits

1. **Version Control**: Track specific versions of dependencies
2. **Consistency**: All external dependencies managed uniformly
3. **Updates**: Easy to update to newer versions
4. **Size**: Reduces repository size by not duplicating large header files

## Fixes

Closes #17

# 44a

This is a template for an openFrameworks project which compiles, and runs in JetBrains' awesome CLion. I've used one of the 3D examples to test this.

## Quick start
Import this as an existing project in CLion, and don't choose the option to re-create the CMakeLists.txt.

## Updating the CMake files for your environment
### Setting your oF root directory
Open CMakeLists.txt, and on line 8, update the path to your oF root path

### Setting your Mac OSX SDK path
At the time of writing this, I was on OSX 10.11. If you find this when you're on a newer version, update line 128 in the file openFrameworks.cmake

## Compatibility
This has been known to work excellently with oF 0.8.4, and CLion 1.1.1

## Credits
All the cmake credit goes to kureta (https://gist.github.com/kureta/b764cb130dafb91375d6). He/she's put in a lot of effort to get it working smoothly. Kudos @kureta!

I've just pieced it together so that beginners might find it easier, and for me to refer to this when creating a new oF project.

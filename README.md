# Native File Dialog CMake

In this fork I replaced Premake and other build system with CMake

For more information look at the original [README.md](https://github.com/mlabbe/nativefiledialog/blob/5cfe5002eb0fac1e49777a17dec70134147931e2/README.md)

## Example

An example of CMakeLists.txt

```cmake
add_subdirectory(libs/nativefiledialog)
add_executable(mytarget main.cpp)
target_link_libraries(mytarget nativefiledialog)
```

and main.cpp

```C
#include <nfd.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    nfdchar_t *outPath = NULL;
    nfdresult_t result = NFD_OpenDialog( NULL, NULL, &outPath );
        
    if ( result == NFD_OKAY ) {
        puts("Success!");
        puts(outPath);
        free(outPath);
    }
    else if ( result == NFD_CANCEL ) {
        puts("User pressed cancel.");
    }
    else {
        printf("Error: %s\n", NFD_GetError() );
    }

    return 0;
}
```

See [NFD.h](src/include/nfd.h) for more options.

# Screenshots #

![Windows 8 rendering an IFileOpenDialog](screens/open_win.png?raw=true)
![GTK3 on Linux](screens/open_gtk3.png?raw=true)
![Cocoa on Yosemite](screens/open_cocoa.png?raw=true)

## Changelog ##

release | what's new                  | date
--------|-----------------------------|---------
1.0.0   | initial                     | oct 2014
1.1.0   | premake5; scons deprecated  | aug 2016
1.1.1   | mingw support, build fixes  | aug 2016
1.1.2   | test_pickfolder() added     | aug 2016
1.1.3   | zenity linux backend added  | nov 2017
1.1.3   | fix char type in decls      | nov 2017
1.1.4   | fix win32 memleaks          | dec 2018
1.1.4   | improve win32 errorhandling | dec 2018
1.1.4   | macos fix focus bug         | dec 2018


# CMake
## Descirption
Build and package software (mostly using c++) with cmake. 

## Installation 
Main-site: https://cmake.org/install/

Homebrew: https://formulae.brew.sh/cask/cmake#default

### CMakeLists.txt
Most of the defined items are specified by the libraries creator.
#### Define OS
```cmake
if(UNIX AND NOT APPLE)
	... # Linux
elseif(APPLE)
	... # APPLE (Mac)
else()
	... # Windows
endif()
```

#### Define minimum version 
Doc: https://cmake.org/cmake/help/latest/command/cmake_minimum_required.html
```cmake
cmake_minimum_required(VERSION "3.19.2")
```

#### Define project name
Doc: https://cmake.org/cmake/help/latest/command/project.html
```cmake
project("project_name")
```

#### Find installed package
Doc: https://cmake.org/cmake/help/latest/command/find_package.html
```cmake
find_package(*package_name* REQUIRED)
```

#### Set source directory
```cmake
set(NAME_SRC
	src/main.cpp
	src/example.cpp)
```

#### Set header directory
```cmake
set(NAME_H
	include/main.h
	include/example.h)
```

#### Set executable output pathexecutable
This will create bin folder if one does not exist.

```cmake
set(EXE_PATH ${CMAKE_BINARY_DIR}/bin)
```

#### Include directories
Can add multiple include directories here.

```cmake
include_directories(${CMAKE_SOURCE_DIR}/include ...)
```

#### Add executable
```cmake
add_executable(${PROJECT_NAME} ${NAME_SRC} ${NAME_H})
```

#### Add compile features
Add custom compile features such as c++ version.

Doc: https://cmake.org/cmake/help/latest/command/target_compile_features.html
```cmake
target_compile_features(${PROJECT_NAME} PUBLIC cxx_std_17)
```

#### Link libraries
Link external libraries to project.

Doc: https://cmake.org/cmake/help/latest/command/target_link_libraries.html
```cmake
target_link_libraries(${PROJECT_NAME} PRIVATE *library_name* ...)
```

#### Target include directories
Difference between target and normal include directories:

Target - links to specific project

Other - global linkage

Doc: https://cmake.org/cmake/help/latest/command/target_include_directories.html
```cmake
target_include_directories(${PROJECT_NAME} PRIVATE *library_name* ...)
```


## CPM-cmake (Package manager)
Adds dependancies to machine upon building cmake.

Github: https://github.com/cpm-cmake/CPM.cmake

Add this to CMakeLists.txt to install CPM:
```cmake
set(CPM_DOWNLOAD_VERSION 0.28.4)

if(CPM_SOURCE_CACHE)
	set(CPM_DOWNLOAD_LOCATION "${CPM_SOURCE_CACHE}/cpm/CPM_${CPM_DOWNLOAD_VERSION}.cmake")
elseif(DEFINED ENV{CPM_SOURCE_CACHE})
	set(CPM_DOWNLOAD_LOCATION "$ENV{CPM_SOURCE_CACHE}/cpm/CPM_${CPM_DOWNLOAD_VERSION}.cmake")
else()
	set(CPM_DOWNLOAD_LOCATION "${CMAKE_BINARY_DIR}/cmake/CPM_${CPM_DOWNLOAD_VERSION}.cmake")
endif()

if(NOT (EXISTS ${CPM_DOWNLOAD_LOCATION}))
	message(STATUS "Downloading CPM.cmake to ${CPM_DOWNLOAD_LOCATION}")
	file(DOWNLOAD
		https://github.com/TheLartians/CPM.cmake/releases/download/v${CPM_DOWNLOAD_VERSION}/CPM.cmake
		${CPM_DOWNLOAD_LOCATION}
	)
endif()

include(${CPM_DOWNLOAD_LOCATION})
```
### Add Package
```cmake
CPMAddPackage(
	NAME          # The unique name of the dependency (should be the exported target's name)
	VERSION       # The minimum version of the dependency (optional, defaults to 0)
	OPTIONS       # Configuration options passed to the dependency (optional)
	DOWNLOAD_ONLY # If set, the project is downloaded, but not configured (optional)
	[...]         # Origin parameters forwarded to FetchContent_Declare, see below
)
```

### Link library
```cmake
if(*library_name*_ADDED)
	add_library(*library_name* INTERFACE IMPORTED)
	target_include_directories(*library_name* INTERFACE ${*library_source_dir})
endif()
```





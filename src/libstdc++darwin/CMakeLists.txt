project(libstdc++darwin)

# clang doesn't support linker scripts (-T)
SET(CMAKE_CXX_COMPILER "/usr/bin/g++")
set(CMAKE_CXX_FLAGS "")

if (SUFFIX STREQUAL "32")
	set(CMAKE_CXX_FLAGS "-m32")
endif (SUFFIX STREQUAL "32")

cmake_minimum_required(VERSION 2.4.0)

add_definitions(-Bsymbolic -fno-weak)
add_library(stdc++darwin SHARED filebuf_abi_fix.cpp)

#add_custom_target(stdc++_darwinx ALL COMMAND echo objcopy
#	--redefine-syms=${CMAKE_CURRENT_SOURCE_DIR}/renames.list
#	${CMAKE_CURRENT_BINARY_DIR}/libstdc++_darwin.so)

#add_dependencies(stdc++_darwinx stdc++_darwin)
#target_link_libraries(stdc++-darwin -T${CMAKE_CURRENT_SOURCE_DIR}/renames.cmd)

install(TARGETS stdc++darwin DESTINATION "lib${SUFFIX}/darling")


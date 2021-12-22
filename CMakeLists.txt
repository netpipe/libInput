cmake_minimum_required(VERSION 3.2)

project(Input)

option(X11_BACKEND "Build X11 Backend" ON)
option(BUILD_EXAMPLES "Build examples" ON)

if (X11_BACKEND)
    message(STATUS "Enabled X11 Backend")
    find_package(X11 COMPONENTS Xau
	Xext Xdmcp Xi
	Xtst Xfixes Xcomposite
	Xrender Xinerama xkbcommon
	REQUIRED)

    find_package(Threads REQUIRED)
endif()

add_subdirectory(src)
add_subdirectory(examples)

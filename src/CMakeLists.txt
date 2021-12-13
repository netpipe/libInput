set(Input_SOURCES InputController.cpp)
set(Input_HEADERS InputController.h  InputDevice.h  Keyboard.h  Mouse.h)

if (X11_BACKEND)
	set(Input_SOURCES ${Input_SOURCES} x11/X11InputController.cpp  x11/X11InputDevice.cpp x11/X11Keyboard.cpp  x11/X11Mouse.cpp)
	set(Input_HEADERS ${Input_HEADERS} x11/X11InputController.h x11/X11InputDevice.h x11/X11Keyboard.h  x11/X11Mouse.h)
endif()

add_library(Input ${Input_SOURCES} ${Input_HEADERS})
	
if (X11_BACKEND)
	target_link_libraries(Input X11 Xi Xext xcb Xau Xdmcp pthread)
endif()

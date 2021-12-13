set(Input_SOURCES InputController.cpp)
set(Input_HEADERS InputController.h  InputDevice.h  Keyboard.h  Mouse.h)

if (X11_BACKEND)
	set(Input_SOURCES ${Input_SOURCES} x11/X11InputController.cpp  x11/X11InputDevice.cpp x11/X11Keyboard.cpp  x11/X11Mouse.cpp)
	set(Input_HEADERS ${Input_HEADERS} x11/X11InputController.h x11/X11InputDevice.h x11/X11Keyboard.h  x11/X11Mouse.h)
endif()

add_library(Input ${Input_SOURCES} ${Input_HEADERS})
	
if (X11_BACKEND)
	find_package(X11 COMPONENTS xcb Xau Xext Xdmcp Xi REQUIRED)
	find_package(Threads REQUIRED)
	target_link_libraries(Input
		${X11_LIBRARIES}
		${X11_xcb_LIB}
		${X11_Xau_LIB}
		${X11_Xdmcp_LIB}
		${X11_Xi_LIB}
		${X11_Xext_LIB}
		Threads::Threads)
endif()

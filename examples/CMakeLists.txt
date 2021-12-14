set(CMAKE_BUILD_TYPE Debug)

add_executable(query_state query_state.cpp)

target_link_libraries(query_state PRIVATE Input)

if (X11_BACKEND)
    target_compile_definitions(query_state PRIVATE USE_X11=1)
endif()

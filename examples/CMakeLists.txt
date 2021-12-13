set(CMAKE_BUILD_TYPE Debug)

add_executable(query_state query_state.cpp)

target_link_libraries(query_state PRIVATE Input -static)
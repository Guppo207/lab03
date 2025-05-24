cmake_minimum_required(VERSION 3.5)
PROJECT(solver_app LANGUAGES CXX)

if(NOT TARGET formatter_ex)
	add_subdirectory(${CMAKE_SOURCE_DIR}/formatter_ex_lib
		${CMAKE_CURRENT_BINARY_DIR}/formatter_ex_lib)
endif()

if(NOT TARGET solver_lib)
	add_subdirectory(${CMAKE_SOURCE_DIR}/solver_lib
		${CMAKE_CURRENT_BINARY_DIR}/solver.lib)
endif()

add_executable(solver equation.cpp)
target_link_libraries(solver PRIVATE formatter_ex solver_lib)

cmake_minimum_required(VERSION 3.23)
project(my_project)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake")

if (NOT DEFINED ENV{GUROBI_HOME} AND NOT DEFINED GUROBI_DIR)
    message(FATAL_ERROR "No cache variable named GUROBI_DIR is defined, and GUROBI_HOME was not found in the environment variables. Please, define one of them.")
endif ()

add_executable(my_target main.cpp)
find_package(GUROBI REQUIRED)
target_link_libraries(my_target PUBLIC gurobi)

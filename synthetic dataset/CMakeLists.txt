cmake_minimum_required(VERSION 2.8)

project(synthetic_data)

add_executable(synthetic_data src/synthetic_dataset.cpp)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_SOURCE_DIR}/cmake)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g -O3   ")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -O3  ")

find_package(CVD)
INCLUDE_DIRECTORIES(${CVD_INCLUDE_DIR})
message(${CVD_INCLUDE_DIR})
link_libraries(${CVD_LIBRARY})
message(${CVD_LIBRARY})

target_link_libraries(synthetic_data ${CVD_LIBRARY})

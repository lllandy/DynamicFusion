cmake_minimum_required(VERSION 2.8)

project(tracking_test)

add_executable(tracking_test src/tracking_test.cpp)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_SOURCE_DIR}/cmake)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g -O3   ")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -O3  ")

find_package(CVD)
find_package(Eigen3 REQUIRED)
find_package(Cholmod)
include_directories(${CHOLMOD_INCLUDES})


INCLUDE_DIRECTORIES(${CVD_INCLUDE_DIR})
message(${CVD_INCLUDE_DIR})
link_libraries(${CVD_LIBRARY})

#------Eigen Version-----#

if(EIGEN3_FOUND)
include_directories(${EIGEN3_INCLUDE_DIR})
link_libraries(${EIGEN3_LIBRARY})

endif(EIGEN3_FOUND)



target_link_libraries(tracking_test ${CVD_LIBRARY})
target_link_libraries(tracking_test ${EIGEN3_LIBRARY})
target_link_libraries(tracking_test ${CHOLMOD_LIBRARIES})

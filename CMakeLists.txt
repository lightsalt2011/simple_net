cmake_minimum_required(VERSION 2.8)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
add_compile_options(-std=c++11) # CMake 2.8.12 or newer
project(SIMPLE_NET)


#opencv
find_package( OpenCV REQUIRED )
include_directories(${OpenCV_INCLUDE_DIRS})

# move_base
add_library(simple_net
  src/Function.cpp
  src/csv2xml.cpp
  src/Net.cpp
)
target_link_libraries(simple_net
    ${OpenCV_LIBS}
    )

add_executable(test examples/test.cpp )
target_link_libraries(test simple_net ${OpenCV_LIBS} ${Boost_LIBRARIES})

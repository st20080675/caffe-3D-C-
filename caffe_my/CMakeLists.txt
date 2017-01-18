cmake_minimum_required(VERSION 2.8.3)
project(caffe_my)

#add_definitions(-std=c++0x -DCPU_ONLY=1)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -O3 -march=native")
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3 -march=native")

#set(CMAKE_CXX_COMPILER /usr/bin/g++-4.6)
set(CAFFE_INCLUDEDIR /home/sunting/Documents/program/3D_recognition/caffe-master/include /home/sunting/Documents/program/3D_recognition/caffe-master/distribute/include)
set(CAFFE_LINK_LIBRARAY /home/sunting/Documents/program/3D_recognition/caffe-master/build/lib)

## System dependencies are found with CMake's conventions
# find_package(Boost REQUIRED COMPONENTS system)
find_package(Boost COMPONENTS system filesystem REQUIRED)
find_package(OpenCV REQUIRED)
find_package(Protobuf REQUIRED)
find_package(PCL 1.2 REQUIRED)
#find_package(Caffe)


###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
# include_directories(include)

include_directories(${PROTOBUF_INCLUDE_DIR})
include_directories(${OPENCV_INCLUDE_DIR})
include_directories(${Boost_INCLUDE_DIR})
include_directories(${PCL_INCLUDE_DIRS})
include_directories(/usr/local/cuda-7.5/targets/x86_64-linux/include)
link_directories(/usr/lib/x86_64-linux-gnu /usr/local/hdf5/lib)

include_directories(${CAFFE_INCLUDEDIR})
link_directories(${CAFFE_LINK_LIBRARAY} ${HDF5_HL_LIBRARIES} ${PCL_LIBRARY_DIRS})

add_executable(caffe_my main.cpp)
target_link_libraries(caffe_my ${Boost_FILESYSTEM_LIBRARY} ${Boost_SYSTEM_LIBRARY} ${OpenCV_LIBRARIES} ${PROTOBUF_LIBRARY} ${HDF5_HL_LIBRARIES} ${PCL_LIBRARIES} caffe glog)


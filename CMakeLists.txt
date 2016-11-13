CMAKE_MINIMUM_REQUIRED (VERSION 3.4)

PROJECT (Demo VERSION 0.0.0)

SET(BUILD_TESTING flase)

#读取Src目录
AUX_SOURCE_DIRECTORY(. DIR_SRCS)

#指定头文件路径
include_directories(${PROJECT_SOURCE_DIR}/Include)

include_directories(/usr/X11/include/)
link_directories(/usr/X11/lib)

#编译文件
ADD_EXECUTABLE(${PROJECT_NAME} ${DIR_SRCS})

#输出路径
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/build/bin)

#链接库
TARGET_LINK_LIBRARIES(${PROJECT_NAME} GL glfw3 glad)

#设置编译选项
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -g -Wall")

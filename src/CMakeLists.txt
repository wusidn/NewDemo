CMAKE_MINIMUM_REQUIRED (VERSION 3.4)

PROJECT (engine VERSION 0.0.1)

SET(BUILD_TESTING flase)

#跨平台测试
IF(WIN32)
    MESSAGE("WIN32")
ELSE(UNIX AND APPLE)
    MESSAGE("MacOS")
ELSE(UNIX)
    MESSAGE("Linux")
ENDIF()

#读取Src目录
AUX_SOURCE_DIRECTORY(. DIR_SRCS)

#编译文件
ADD_LIBRARY(${PROJECT_NAME} ${DIR_SRCS})

#输出路径
SET(LIBRARY_OUTPUT_PATH ${PROJECT_ROOT_DIR}/build/bin)

#链接库
TARGET_LINK_LIBRARIES(${PROJECT_NAME} glfw3 glad)

#设置编译选项
if(WIN32)
    SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -std=c++11 -Wall")
    SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -std=c++11 -Wall")
elseif(UNIX)
    SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -std=c++11 -O0 -Wall -g")
    SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -std=c++11 -O3 -Wall")
endif()

cmake_minimum_required(VERSION 3.10)
project(VSS-AI)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread") 

find_package(Boost REQUIRED COMPONENTS system)

include_directories("${CMAKE_SOURCE_DIR}/include"
                    "${CMAKE_SOURCE_DIR}/lib"
                    ${Boost_INCLUDE_DIRS})

set(SRCS
    "src/geometry/vector_2d.cc")

add_library(${PROJECT_NAME}_SRCS
            ${SRCS})

set (VSS_CORE libvss-core.so)

add_executable(${PROJECT_NAME} "src/main.cpp")

target_link_libraries(${PROJECT_NAME}
                    ${PROJECT_NAME}_SRCS
                    ${VSS_CORE}
                    ${Boost_LIBRARIES})
cmake_minimum_required(VERSION 3.16)

set(PROTOBUF protobuf)
project(${PROTOBUF})

set(WRITING protobuf_write)
set(READING protobuf_read)

set (CMAKE_CXX_STANDARD 11)


set(SHARED_SRC protobuf_files/addressbook.pb.cc)

add_executable(${WRITING} 
    src/main_write.cpp
    ${SHARED_SRC}
)

add_executable(${READING} 
    src/main_read.cpp
    ${SHARED_SRC}
)

include_directories(
    ${${PROTOBUF}_SOURCE_DIR}/protobuf_files 
    ${${PROTOBUF}_SOURCE_DIR}/../protobuf/src 
)

set(LIBS
    ${${PROTOBUF}_SOURCE_DIR}/../protobuf/cmake/build/libprotobuf.a
    ${${PROTOBUF}_SOURCE_DIR}/../protobuf/cmake/build/libprotobuf-lite.a
    ${${PROTOBUF}_SOURCE_DIR}/../protobuf/cmake/build/libprotoc.a
)

target_link_libraries( ${WRITING} ${LIBS} )
target_link_libraries( ${READING} ${LIBS} )

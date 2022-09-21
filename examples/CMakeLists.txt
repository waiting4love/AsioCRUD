# -*- cmake -*-

cmake_minimum_required(VERSION 3.3.2)

set(ASIO_INCLUDE_DIR "${PROJECT_SOURCE_DIR}/asio-1.24.0/include")
include_directories(${ASIO_INCLUDE_DIR} ${PROJECT_SOURCE_DIR})

set(SYSLIBS ws2_32 Mswsock)

add_executable(
        regex_restful_service
        regex_restful_service.cpp
        )

add_executable(
        simple_restful_service
        simple_restful_service.cpp
        )

add_executable(
        persisted_regex_restful_service
        persisted_regex_restful_service.cpp
        )

add_executable(
        webserver 
        webserver.cpp
        )

find_package (Threads)

target_link_libraries(
        regex_restful_service
        crud_service
        ${CMAKE_THREAD_LIBS_INIT}
        ${SYSLIBS}
        )

target_link_libraries(
        simple_restful_service
        crud_service
        ${CMAKE_THREAD_LIBS_INIT}
        ${SYSLIBS}
        )

target_link_libraries(
        persisted_regex_restful_service
        crud_service
        ${CMAKE_THREAD_LIBS_INIT}
        ${SYSLIBS}
        )


target_link_libraries(
        webserver 
        crud_service
        ${CMAKE_THREAD_LIBS_INIT}
        ${SYSLIBS}
        )


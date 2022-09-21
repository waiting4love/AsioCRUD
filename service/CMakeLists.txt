
set(CMAKE_CXX_STANDARD 14)

## Configuring Boost

set(ASIO_INCLUDE_DIR "${PROJECT_SOURCE_DIR}/asio-1.24.0/include")

include_directories(${ASIO_INCLUDE_DIR})

include_directories(../handlers)

if (WIN32)
    # DLLs in Windows appear to have not been fully thought through
    set(DEFAULT_LIBRARY_TYPE "STATIC")
else()
    set(DEFAULT_LIBRARY_TYPE "SHARED")
endif()

add_library(crud_service
            ${DEFAULT_LIBRARY_TYPE}
	    mime_types.cpp
	    reply.cpp
	    request_handler.cpp
	    request_parser.cpp
           )
find_package (Threads)

target_link_libraries( crud_service ${CMAKE_THREAD_LIBS_INIT})

install(TARGETS crud_service
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
)


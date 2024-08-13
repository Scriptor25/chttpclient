project(CHTTP)

option(CHTTP_BUILD_EXAMPLE "Build the example executable target" OFF)
option(CHTTP_INSTALL "Build the install target" OFF)

file(GLOB_RECURSE src src/*.c include/*.h)
add_library(chttp ${src})
target_include_directories(chttp PUBLIC include)

if(CHTTP_BUILD_EXAMPLE)
	add_executable(CHTTPClientSample example/HTTPClientSample.c example/HTTPClientSample.h)
	target_include_directories(CHTTPClientSample PRIVATE example)
	target_link_libraries(CHTTPClientSample PRIVATE chttp)
endif()

if(CHTTP_INSTALL)
	install(TARGET chttp)
endif()

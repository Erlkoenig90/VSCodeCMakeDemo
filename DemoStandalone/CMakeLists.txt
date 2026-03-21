cmake_minimum_required(VERSION 3.28)

set(CMAKE_LINK_LIBRARIES_ONLY_TARGETS ON)
set(CMAKE_VERBOSE_MAKEFILE ON CACHE BOOL "ON" FORCE)
set(CMAKE_EXPORT_COMPILE_COMMANDS TRUE)

if(CMAKE_VERSION VERSION_GREATER_EQUAL "4.2.0") 
	cmake_policy(SET CMP0200 NEW)
	cmake_policy(SET CMP0199 NEW)
endif()

if(CMAKE_VERSION VERSION_GREATER_EQUAL "4.0") 
	cmake_policy(SET CMP0181 NEW)
endif()


if(CMAKE_VERSION VERSION_GREATER_EQUAL "3.31") 
	cmake_policy(SET CMP0179 NEW)
endif()

if(CMAKE_VERSION VERSION_GREATER_EQUAL "3.29") 
	cmake_policy(SET CMP0156 NEW)
endif()

set(CMAKE_CXX_STANDARD "23")
set(CMAKE_C_STANDARD "23")
add_compile_options("$<$<CXX_COMPILER_ID:MSVC>:/W4;/Zc:preprocessor;/nologo>")

project("DemoStandalone")

enable_language(C CXX)

add_executable(${PROJECT_NAME})
target_sources(${PROJECT_NAME} PRIVATE "main.c")

install(TARGETS ${PROJECT_NAME})

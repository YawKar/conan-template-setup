cmake_minimum_required(VERSION 3.15)
project(conan_template CXX)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(fmt REQUIRED)

set(SRCS src/main.cpp)

add_executable(${PROJECT_NAME} ${SRCS})

if(MSVC)
  target_compile_options(${PROJECT_NAME} PRIVATE /W4 /WX)
else()
  target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Wpedantic -Werror -Wshadow -Wconversion)
endif()

target_link_libraries(${PROJECT_NAME} fmt::fmt)


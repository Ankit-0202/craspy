cmake_minimum_required(VERSION 3.20)
project(Scripty)

# Set the C++ standard (optional)
set(CMAKE_CXX_STANDARD 20)

# Set the root directory
set(PROJECT_ROOT ${CMAKE_CURRENT_SOURCE_DIR})

# Set the include and source directories
set(INCLUDE_DIR ${PROJECT_ROOT}/include)
set(SOURCE_DIR ${PROJECT_ROOT}/src)

# Set the build directory
set(BUILD_DIR ${PROJECT_ROOT}/build)
set(BINARY_DIR ${PROJECT_ROOT}/bin)

# Collect all the header files
file(GLOB_RECURSE HEADER_FILES ${INCLUDE_DIR}/*.hpp)

# Collect all the source files
file(GLOB_RECURSE SOURCE_FILES ${SOURCE_DIR}/*.cpp)

# Set the output directory for object files
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${BUILD_DIR})

# Set the output directory for the final executable (optional)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${BINARY_DIR})

# Add the include directories
include_directories(${INCLUDE_DIR})

# Set compile/link options
add_compile_options(-g -Wall -Werror -fsanitize=address)
add_link_options(-g -Wall -Werror -fsanitize=address)

# Create the executable from source files
add_executable(${PROJECT_NAME} ${SOURCE_FILES} ${HEADER_FILES})

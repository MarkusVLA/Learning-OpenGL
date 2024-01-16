cmake_minimum_required(VERSION 3.3)
project(OpenGL)

set(CMAKE_CXX_STANDARD 17)

# Find the OpenGL package
find_package(OpenGL REQUIRED)

# Add the GLFW submodule
add_subdirectory(libs/glfw)

# Add GLAD
add_library(glad STATIC libs/glad/src/glad.c)
target_include_directories(glad PRIVATE libs/glad/include)

# Include directories
include_directories(${OPENGL_INCLUDE_DIR})
include_directories(libs/glad/include)
include_directories(libs/glfw/include)

# Your executable
add_executable(app src/main.cpp)

# Link against OpenGL, GLFW, and GLAD
target_link_libraries(app ${OPENGL_gl_LIBRARY} glfw glad)

cmake_minimum_required(VERSION 3.10)

# set the project name and version
project(Tutorial VERSION 1.0)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Any file to pass into code as a header file
configure_file(TutorialConfig.h.in TutorialConfig.h)

# add the MathFunctions library
add_subdirectory(MathFunctions)

# add the executable
add_executable(HelloWorld HelloWorld.cpp)

target_link_libraries(HelloWorld PUBLIC MathFunctions)

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(HelloWorld PUBLIC
                           "${PROJECT_BINARY_DIR}"
			   "${PROJECT_BINARY_DIR}/MathFunctions"
                           )

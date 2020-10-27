cmake_minimum_required(VERSION 3.13)
project(cmake_testapp)

set(CMAKE_CXX_STANDARD 14)


## https://www.jetbrains.com/help/clion/quick-cmake-tutorial.html#addtargets-reload
add_executable(cmake_testapp main.cpp)
#add_executable(cmake_testapp_calc main.cpp calc.cpp)
add_executable(cmake_testapp_calc calc.cpp)
#
## https://www.jetbrains.com/help/clion/quick-cmake-tutorial.html#lib-targets
add_library (test_library STATIC calc.cpp)
#
## https://www.jetbrains.com/help/clion/quick-cmake-tutorial.html#inc-dirs
#include_directories (D:/lib/boost_1_74_0/boost_1_74_0)
include_directories (includes/general)
include_directories (includes/math)

#
## https://www.jetbrains.com/help/clion/quick-cmake-tutorial.html#static-libs
find_library(TEST_LIBRARY test_library lib)
find_library(TEST_LIBRARY test_library cmake-build-debug)
target_link_libraries(cmake_testapp LINK_PUBLIC ${TEST_LIBRARY})
#
## https://www.jetbrains.com/help/clion/quick-cmake-tutorial.html#boost

#list(APPEND CMAKE_PREFIX_PATH "D:\\lib\\boost_1_74_0\\boost_1_74_0")

target_include_directories(cmake_testapp PUBLIC
        "${PROJECT_BINARY_DIR}"
        )


#add_subdirectory(test)
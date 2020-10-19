set (Boost_USE_STATIC_LIBS OFF) #enable dynamic linking


set (Boost_DETAILED_FAILURE_MSG ON)
set (Boost_THREADAPI win32)
set (BOOST_ROOT "D:\\lib\\boost_1_67_0\\boost_1_67_0")
set (Boost_LIBRARY_DIR  "D:\\lib\\boost_1_67_0\\boost_1_67_0\\lib")
set (Boost_LIBRARY_DIR  "D:\\lib\\boost_1_67_0\\boost_1_67_0\\stage\\lib")
set (Boost_COMPILER "-vc")
set (Boost_USE_STATIC_RUNTIME ON)
set (Boost_DEBUG ON)  #<---------- Real life saver


include_directories(${Boost_INCLUDE_DIR})
include_directories(${Boost_LIBRARY_DIR})
include_directories(D:\\lib\\boost_1_67_0\\boost_1_67_0)
include_directories(D:\\lib\\boost_1_67_0\\boost_1_67_0\\stage\\lib)



#search for unit_test_framework
#find_package (Boost REQUIRED COMPONENTS unit_test_framework)



#create a cmake_testapp_boost target from test.cpp
add_executable (cmake_testapp_boost tests.cpp)

#link Boost libraries to the new target
target_link_libraries (cmake_testapp_boost ${Boost_LIBRARIES})

#link Boost with code library
target_link_libraries (cmake_testapp_boost test_library)
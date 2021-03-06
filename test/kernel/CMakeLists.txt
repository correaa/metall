add_executable(named_object_directory_test named_object_directory_test.cpp)
target_link_libraries(named_object_directory_test gtest_main)
gtest_discover_tests(named_object_directory_test)

add_executable(bin_manager_test bin_manager_test.cpp)
target_link_libraries(bin_manager_test gtest_main)
gtest_discover_tests(bin_manager_test)

add_executable(bin_directory_test bin_directory_test.cpp)
target_link_libraries(bin_directory_test gtest_main)
gtest_discover_tests(bin_directory_test)

add_executable(multilayer_bitset_test multilayer_bitset_test.cpp)
target_link_libraries(multilayer_bitset_test gtest_main)
gtest_discover_tests(multilayer_bitset_test)

add_executable(chunk_directory_test chunk_directory_test.cpp)
target_link_libraries(chunk_directory_test gtest_main)
gtest_discover_tests(chunk_directory_test)

add_executable(manager_test manager_test.cpp)
target_link_libraries(manager_test gtest_main)
gtest_discover_tests(manager_test)

if (NOT RUN_BUILD_AND_TEST_WITH_CI)
    add_executable(snapshot_test snapshot_test.cpp)
    target_link_libraries(snapshot_test gtest_main)
    gtest_discover_tests(snapshot_test)
endif()

if (NOT RUN_BUILD_AND_TEST_WITH_CI)
    add_executable(copy_file_test copy_file_test.cpp)
    target_link_libraries(copy_file_test gtest_main)
    gtest_discover_tests(copy_file_test)
endif()

find_package(OpenMP)
if (OPENMP_FOUND)
    set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")

    add_executable(manager_multithread_test manager_multithread_test.cpp)
    target_link_libraries(manager_multithread_test gtest_main)
    gtest_discover_tests(manager_multithread_test)
else()
    MESSAGE(WARNING "OpenMP is not found. Use single thread in the test")
endif()

add_executable(multimanager_test multimanager_test.cpp)
target_link_libraries(multimanager_test gtest_main)
gtest_discover_tests(multimanager_test)
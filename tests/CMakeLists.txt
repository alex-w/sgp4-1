add_executable(sgp4_tests
    test_util.cc
    test_timespan.cc
    test_vector.cc
    test_datetime.cc
    test_tle.cc
    test_sgp4.cc)

target_link_libraries(sgp4_tests PRIVATE sgp4 gtest_main)

gtest_discover_tests(sgp4_tests)

add_executable(runtest runtest.cc)
target_link_libraries(runtest PRIVATE SGP4::sgp4)

add_test(NAME SGP4Verification COMMAND runtest
    WORKING_DIRECTORY "${PROJECT_BINARY_DIR}")

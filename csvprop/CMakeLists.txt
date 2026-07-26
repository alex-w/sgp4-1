add_executable(csvprop csvprop.cc)
target_link_libraries(csvprop PRIVATE SGP4::sgp4)
target_compile_definitions(csvprop PRIVATE
    CSV_DATA_DIR="${CMAKE_CURRENT_SOURCE_DIR}/../data")

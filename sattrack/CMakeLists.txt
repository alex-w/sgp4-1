add_executable(sattrack sattrack.cc)
target_link_libraries(sattrack PRIVATE SGP4::sgp4)

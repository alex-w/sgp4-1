add_executable(passpredict passpredict.cc)
target_link_libraries(passpredict PRIVATE SGP4::sgp4)

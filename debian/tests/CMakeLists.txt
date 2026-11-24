cmake_minimum_required(VERSION 3.19)

project(hyprcursor-tests LANGUAGES C CXX)

enable_testing()

find_package(PkgConfig REQUIRED)
pkg_check_modules(deps REQUIRED IMPORTED_TARGET hyprcursor cairo)

add_executable(hyprcursor_test1 tests/full_rendering.cpp)
target_link_libraries(hyprcursor_test1 PRIVATE PkgConfig::deps)
add_test(NAME hyprcursor_test1 COMMAND hyprcursor_test1)

add_executable(hyprcursor_test2 tests/only_metadata.cpp)
target_link_libraries(hyprcursor_test2 PRIVATE PkgConfig::deps)
add_test(NAME hyprcursor_test2 COMMAND hyprcursor_test2)

add_executable(hyprcursor_test_c tests/c_test.c)
target_link_libraries(hyprcursor_test_c PRIVATE PkgConfig::deps)
add_test(NAME hyprcursor_test_c COMMAND hyprcursor_test_c)

cmake_minimum_required(VERSION 3.10)

project(dvode LANGUAGES Fortran VERSION 0.1.0)

add_library(dvode src/dvode_f90_m.f90)

enable_testing()
set(DVODE_TESTS example1 example2)
foreach(D_TEST ${DVODE_TESTS})
  add_executable(${D_TEST} "test/${D_TEST}.f90") 
  target_link_libraries(${D_TEST} dvode)
  add_test(NAME ${D_TEST} COMMAND "./${D_TEST}")
endforeach()
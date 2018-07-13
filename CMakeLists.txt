# CMakeLists.txt in src
cmake_minimum_required(VERSION 2.8)

project(curve-worm)

# cxx11
include(CheckCXXCompilerFlag)
CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11)
CHECK_CXX_COMPILER_FLAG("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
if(COMPILER_SUPPORTS_CXX11)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
elseif(COMPILER_SUPPORTS_CXX0X)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
else()
        message(STATUS "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
endif()

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake-modules/")

# maths
link_libraries(m)
link_libraries(rt)
link_libraries(gfortran)

# SuiteSparse libraries
find_package( SuiteSparse OPTIONAL_COMPONENTS UMFPACK )
include_directories(${SuiteSparse_INCLUDE_DIRS})
link_libraries( ${SuiteSparse_LIBRARIES} )

# blas
find_package( BLAS REQUIRED )
include_directories(${BLAS_INCLUDE_DIR})
link_libraries( ${BLAS_LIBRARIES} )

# lapack
find_package( LAPACK REQUIRED )
include_directories(${LAPACK_INCLUDE_DIR})
link_libraries( ${LAPACK_LIBRARIES} )

# worm model
add_executable(worm-model "worm-model.cc")
target_compile_definitions( worm-model PRIVATE WORLD_DIM=2 )

# configure a header file to pass some of the CMake settings
# to the source code
configure_file (
  "${PROJECT_SOURCE_DIR}/config.hh.in"
  "${PROJECT_BINARY_DIR}/config.hh"
  )
# add the binary tree to the search path for include files
# so that we will find config.hh
include_directories("${PROJECT_BINARY_DIR}")

# symlink scripts
file( GLOB SCRIPTS "${CMAKE_CURRENT_SOURCE_DIR}/scripts/*.sh" )
foreach( script ${SCRIPTS} )
  message(STATUS ${script})
  get_filename_component(base_name ${script} NAME)
  message(STATUS ${base_name})

  execute_process(COMMAND ${CMAKE_COMMAND} -E create_symlink
    ${script} ${CMAKE_CURRENT_BINARY_DIR}/${base_name})
endforeach()

# tests
enable_testing()

add_executable(umfpack-simple "umfpack-simple.cc")
add_test( "umfpack_test" umfpack-simple )

add_test( "worm-model_end2end"
  ./worm-model ../data/model-parameters )
# todo add comparison test when confirmed what we want
# add_test( "worm-model_comparison"
#   COMMAND ${CMAKE_COMMAND} -E compare_files ? ? )

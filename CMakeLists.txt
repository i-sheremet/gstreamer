cmake_minimum_required(VERSION 3.2.2)
project(gstreamer_test_project)

# C++11 Flags
#
add_compile_options(-std=c++11)
add_compile_options(-pthread)
add_compile_options(-Werror=return-type)                   # error on missing return type
add_compile_options(-Werror=format)                        # error on wrong printf formats
add_compile_options(-Werror=parentheses)                   # error when using ambiguous syntax
add_compile_options(-Werror=reorder)                       # error on wrong constructor initialization order

set(STRICT_GCC_FLAGS "\
    -Wunused-but-set-parameter \
    -Wunused-but-set-variable \
    -Wunused-function \
    -Wunused-variable \
    -Wuninitialized \
    -Wmaybe-uninitialized \
    -Wno-endif-labels \
    -Wmissing-field-initializers \
")

find_package(PkgConfig REQUIRED)
pkg_check_modules(GSTREAMER REQUIRED gstreamer-1.0)
include_directories(${GSTREAMER_INCLUDE_DIRS})


### EXECUTABLES #######################################################################################################
add_executable(gstream_test ${CMAKE_CURRENT_LIST_DIR}/gstream_test.cpp)
target_link_libraries(gstream_test ${GSTREAMER_LIBRARIES})

add_executable(basic-tutorial-1 ${CMAKE_CURRENT_LIST_DIR}/basic-tutorial-1.cpp)
target_link_libraries(basic-tutorial-1 ${GSTREAMER_LIBRARIES})

add_executable(basic-tutorial-2 ${CMAKE_CURRENT_LIST_DIR}/basic-tutorial-2.cpp)
target_link_libraries(basic-tutorial-2 ${GSTREAMER_LIBRARIES})

add_executable(basic-tutorial-3 ${CMAKE_CURRENT_LIST_DIR}/basic-tutorial-3.cpp)
target_link_libraries(basic-tutorial-3 ${GSTREAMER_LIBRARIES})

project(sfmltest)
cmake_minimum_required(VERSION 3.1.2)

# pull in the generated conan cmake
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

add_executable(sfmltest sfmltest.cpp)
target_link_libraries(sfmltest CONAN_PKG::SFML)

add_custom_command(TARGET sfmltest POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E copy_directory
  "${PROJECT_SOURCE_DIR}/shaders/"
  $<TARGET_FILE_DIR:sfmltest>)


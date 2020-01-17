cmake_minimum_required(VERSION 3.12...3.15)
project(MaddEngine VERSION 0.1 DESCRIPTION "Madd game engine" LANGUAGES CXX)

set(SOURCE_FILES "")
include(sources.cmake)

add_library(madd SHARED ${SOURCE_FILES})
target_compile_features(madd PUBLIC cxx_std_17)
set_target_properties(madd PROPERTIES CXX_EXTENSIONS OFF)
target_include_directories(madd PUBLIC include)

if(MSVC)
  target_compile_options(madd PRIVATE /W4 /WX /O3)
else()
  target_compile_options(madd PRIVATE -Wall -Wextra -Wpedantic -O3)
endif()

cmake_minimum_required(VERSION 3.20)

project(CarMon)


add_library(
    CarMon
    SHARED
    ${CMAKE_CURRENT_SOURCE_DIR}/src/CarMon.cpp
)

target_include_directories(
    CarMon
    PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_link_libraries(
    CarMon
    PUBLIC
    hashfunc
    utility
)

# test executable
add_executable(test_CarMon ${CMAKE_CURRENT_SOURCE_DIR}/src/test_CarMon.cpp)

target_link_libraries(
    test_CarMon
    PRIVATE
    CarMon
    mylibpcap
)

add_executable(ParamSetting ${CMAKE_CURRENT_SOURCE_DIR}/src/ParameterSetting.cpp)

target_link_libraries(
    ParamSetting
    PRIVATE
    CarMon
    mylibpcap
)
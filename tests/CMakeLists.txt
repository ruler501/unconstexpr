cmake_minimum_required(VERSION 3.14)

include(CTest)

project(unconstexpr_tests
        LANGUAGES CXX)

if (BUILD_TESTING)
    add_executable(${PROJECT_NAME} src/main.cpp)
    target_sources(${PROJECT_NAME} PRIVATE include/unconstexpr/tools/auto_testing.hpp
                                           include/unconstexpr/tools/println.hpp
                                           include/unconstexpr/tools/type_printer.hpp)
    target_link_libraries(${PROJECT_NAME} PRIVATE unconstexpr)
    target_include_directories(${PROJECT_NAME} PRIVATE include)
    target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_17)

    add_test(NAME ${PROJECT_NAME} COMMAND ${PROJECT_NAME})
endif()
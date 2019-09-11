cmake_minimum_required(VERSION 3.14)

project(unconstexpr
        VERSION 0.9.0
        DESCRIPTION "Implementation of mutable constexpr functions"
        HOMEPAGE_URL https://github.com/ruler501/unconstexpr
        LANGUAGES CXX)

add_library(${PROJECT_NAME} INTERFACE)

target_sources(${PROJECT_NAME} INTERFACE include/unconstexpr/meta_any.hpp
                                         include/unconstexpr/meta_counter.hpp
                                         include/unconstexpr/meta_partial.hpp
                                         include/unconstexpr/meta_tlist.hpp
                                         include/unconstexpr/meta_type.hpp
                                         include/unconstexpr/meta_value.hpp
                                         include/unconstexpr/meta_vlist.hpp
                                         include/unconstexpr/unconstexpr.hpp
                                         include/unconstexpr/uniq_value.hpp
                                         include/unconstexpr/tools/type_list.hpp
                                         include/unconstexpr/tools/type_map.hpp
                                         include/unconstexpr/tools/type_string.hpp
                                         include/unconstexpr/tools/var_list.hpp)
target_compile_features(${PROJECT_NAME} INTERFACE cxx_std_17)
target_include_directories(${PROJECT_NAME} INTERFACE include)

option(ENABLE_UNCONSTEXPR_TESTS "Enable running the unconstexpr tests." ON)

if (ENABLE_UNCONSTEXPR_TESTS)
    add_subdirectory(tests)
endif()
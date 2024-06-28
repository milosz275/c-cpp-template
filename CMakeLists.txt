cmake_minimum_required(VERSION 3.18)

set(PROJECT_NAME Projectname)
project(${PROJECT_NAME} C CXX ASM)
project(PRERELEASE VERSION 0.1.0)
set(CMAKE_EXPORT_COMPILE_COMMANDS TRUE)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

add_executable(${PROJECT_NAME}
    project-name/src/main.c
    # project-name/src/main.cpp
)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
    #sfml-graphics
)

target_include_directories(${PROJECT_NAME} PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}
    ${CMAKE_CURRENT_LIST_DIR}/project-name/src
    ${CMAKE_CURRENT_LIST_DIR}/project-name/include
)

# GCC
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    add_compile_options(-O2 -g3
        -Wall
        -Wno-unused-result
        -Wno-format
        -Wno-unused-function
        -Wno-maybe-uninitialized
        -Werror
    )
endif()

# Clang
if(CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    add_compile_options(-O2 -g3
        -Wall
        -Wno-unused-result
        -Wno-format
        -Werror
    )
endif()

# Microsoft Visual C++
if(MSVC)
    add_compile_options(/W4
        /WX
    )
endif()

add_subdirectory(project-name/src)

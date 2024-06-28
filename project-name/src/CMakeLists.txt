cmake_minimum_required(VERSION 3.18)

message("CMAKE_PROJECT_VERSION = ${CMAKE_PROJECT_VERSION}")
set(PROGRAM_NAME projectname)

add_executable(${PROGRAM_NAME}
    main.c
    # main.cpp
)

target_link_libraries(${PROGRAM_NAME}
    PRIVATE
    #sfml-graphics
)

target_include_directories(${PROGRAM_NAME}
    PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}
    ${CMAKE_CURRENT_LIST_DIR}/../include
)

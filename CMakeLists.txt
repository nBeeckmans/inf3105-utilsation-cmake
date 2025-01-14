cmake_minimum_required(VERSION 3.27)
project(#[[nom du projet]])

set(CMAKE_CXX_STANDARD 11)

add_executable(#[[nom de l'executable]]
       #[[
	liste des fichiers à compiler
       ]] 
)

# si vous avez des tests dans un dossier que vous voulez copier dans le dossier 
# de build.

add_custom_target (
        copy_tests
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ${CMAKE_SOURCE_DIR}/tests ${CMAKE_CURRENT_BINARY_DIR}/tests
)

add_dependencies(#[[nom de l'executable]] copy_tests)

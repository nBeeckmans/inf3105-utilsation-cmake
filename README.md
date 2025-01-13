# inf3105-utilsation-cmake

Ceci est un exemple de template de CMAKE qui peut-être utilisé lors du cadre du cours INF3105 pour utilisation cross-platform et/ou avec CLion. 
Ceci ne remplace pas les `Makefiles` donnés lors des TPs et ne doit en **AUCUN CAS** remplacer ces `Makefiles`.


## Template :

```cmake
cmake_minimum_required(VERSION 3.27)
project(#[[nom du projet]])

set(CMAKE_CXX_STANDARD 20)

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
```

## Explications : 

- `cmake\_minimum\_required(VERSION 3.27)` : permet de donner la version de CMAKE minimum nécessaire pour compiler. 
- `project()` : definit un projet 
- `set(CMAKE\_CXX\_STANDARD 20)` : donne le standard C++  
- `add_executable` : ajoute un exécutable à compiler
- `add_custom_target` : crée une commande à exécuter (dans notre cas une copie de dossier récursive)
- `add_dependencies` : ajoute une dépendence à notre exécutable (ainsi, cmake va copier le dossier de tests avant de compiler le programme) 

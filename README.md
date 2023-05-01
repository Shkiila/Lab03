# TIMP_Lab3
## Задание №1
```
cmake_minimum_required(VERSION 3.4)
project(formatter)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(formatter STATIC formatter.cpp formatter.h)
```
## Задание №2
```
cmake_minimum_required(VERSION 3.4)
project(formatter_ex_lib)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(formatter_ex_lib STATIC formatter_ex.cpp )
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib formatter)  
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib)
target_link_libraries(formatter_ex_lib formatter)
```
## Задание №3
```
cmake_minimum_required(VERSION 3.4)
project(hello_world)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex_lib)  
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib)

add_executable(hello_world hello_world.cpp)
target_link_libraries(hello_world formatter_ex_lib)
```
```
cmake_minimum_required(VERSION 3.4)
project(solver_lib)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(solver_lib STATIC solver.cpp solver.h)
```
```
cmake_minimum_required(VERSION 3.4)
project(solver)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex_lib)  
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib solver_lib)  
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib)

add_executable(solver equation.cpp)
target_link_libraries(solver formatter_ex_lib)
target_link_libraries(solver solver_lib)
```

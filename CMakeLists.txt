# c++ -shared -fPIC -std=c++11 -I /home/wu/src/pybind11/include/ `python-config --cflags --ldflags` example.cpp -o example.so

cmake_minimum_required(VERSION 2.8)
include(FindPkgConfig)
#set(Python_ADDITIONAL_VERSIONS 3.7 3.6 3.5 3.4)#if use python3
set(pybind_path  /home/wu/src/pybind11)
list(APPEND CMAKE_MODULE_PATH ${pybind_path}/tools)
find_package(PythonLibsNew ${PYBIND11_PYTHON_VERSION} REQUIRED)
include(pybind11Tools)  
include_directories(${pybind_path}/include)
pybind11_add_module(example example.cpp)

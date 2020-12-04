cmake_minimum_required(VERSION 2.8.3)
project(mydemo)

SET(CMAKE_INSTALL_PREFIX /usr/local/flytos/flytapps CACHE PATH "Cmake install prefix path for flytapps" FORCE)

add_definitions(-std=c++11)

find_package(catkin REQUIRED COMPONENTS cpp_api)
find_package(Boost REQUIRED COMPONENTS system python)
find_package(PythonLibs 2.7 REQUIRED)
include_directories(${catkin_INCLUDE_DIRS} ${PYTHON_INCLUDE_DIRS})

add_executable(mydemo mydemo.cpp)
target_link_libraries(mydemo ${catkin_LIBRARIES} ${Boost_LIBRARIES} ${PYTHON_LIBRARIES}) 

install(TARGETS mydemo
  DESTINATION /flyt/flytapps/onboard/install COMPONENT Runtime
)

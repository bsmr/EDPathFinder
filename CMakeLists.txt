cmake_minimum_required(VERSION 3.5)
project(EliteTSP)
set(ORTOOLS ../or-tools/)
include_directories(${ORTOOLS}/include)
link_directories(${ORTOOLS}/lib)
find_package(Qt5Widgets REQUIRED)
link_libraries(ortools  Qt5::Widgets)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

if(UNIX)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11  -mmacosx-version-min=10.8 -stdlib=libc++  -DARCH_K8 -Wno-deprecated")
else()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_SILENCE_STDEXT_HASH_DEPRECATION_WARNINGS")
endif()

set(SOURCE_FILES src/main.cpp src/System.cpp src/System.h src/tsp.cpp src/MainWindow.cpp src/RouteViewer.cpp src/RouteViewer.ui src/MainWindow.ui resources/resources.qrc)
add_executable(EliteTSP ${SOURCE_FILES})
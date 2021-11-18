cmake_minimum_required(VERSION 3.2)

project(TestProject)

set(CMAKE_CXX_STANDARD 14)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)


find_package(Qt5 COMPONENTS Core REQUIRED)
find_package(Qt5 COMPONENTS Gui REQUIRED)
find_package(Qt6 COMPONENTS Widgets REQUIRED)
find_package(Qt6 COMPONENTS Xml REQUIRED)

set ( SOURCES
main.cpp
    encdec.cpp
    mainwindow.cpp
    passwordwindow.cpp
)

set ( MOC_HEADERS
    encdec.h
    mainwindow.h
    passwordwindow.h
)

set ( UIS
    mainwindow.ui
    passwordwindow.ui
)

QT5_WRAP_UI( UI_HEADERS ${UIS} )

add_executable( PROJECT_NAME ${SOURCES} ${MOC_SRCS} ${UI_HEADERS} )

target_link_libraries(TestProject
    Qt5::Widgets
)

target_link_libraries(TestProject Qt5::Gui)
target_link_libraries(TestProject Qt5::Core)
target_link_libraries(TestProject PRIVATE Qt6::Widgets)
target_link_libraries(TestProject PRIVATE Qt6::Xml)
cmake_minimum_required(VERSION 3.10)

project(ShowJCR VERSION 0.1 LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find the required Qt packages
find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS 
    Core
    Gui
    Widgets
    Sql              # Add this for database support
    Network          # Add if you need network features
)

find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS 
    Core
    Gui
    Widgets
    Sql              # Add this for database support
    Network          # Add if you need network features
)

# Your source files
set(PROJECT_SOURCES
    main.cpp
    showjcr.cpp
    showjcr.h
    showjcr.ui
    sqlitedb.cpp
    sqlitedb.h
    aboutdialog.cpp
    aboutdialog.h
    aboutdialog.ui
    resources/resources.qrc
)

# Create the executable
if(WIN32)
    add_executable(ShowJCR WIN32  # Add WIN32 here to specify Windows GUI application
        ${PROJECT_SOURCES}
    )
else()
    add_executable(ShowJCR
        ${PROJECT_SOURCES}
    )
endif()

# Link against the Qt libraries
target_link_libraries(ShowJCR PRIVATE
    Qt${QT_VERSION_MAJOR}::Core
    Qt${QT_VERSION_MAJOR}::Gui
    Qt${QT_VERSION_MAJOR}::Widgets
    Qt${QT_VERSION_MAJOR}::Sql       # Add this for database support
    Qt${QT_VERSION_MAJOR}::Network   # Add if you need network features
)

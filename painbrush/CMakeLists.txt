# Copyright (C) 2022 The Qt Company Ltd.
# SPDX-License-Identifier: BSD-3-Clause

cmake_minimum_required(VERSION 3.16)
project(paintbrush LANGUAGES CXX)

find_package(Qt6
    REQUIRED COMPONENTS Core Gui Widgets
    OPTIONAL_COMPONENTS PrintSupport
)

qt_standard_project_setup()

qt_add_executable(paintbrush
    main.cpp
    mainwindow.cpp mainwindow.h
    scribblearea.cpp scribblearea.h
)

set_target_properties(paintbrush PROPERTIES
    WIN32_EXECUTABLE TRUE
    MACOSX_BUNDLE TRUE
)

target_link_libraries(paintbrush PRIVATE
    Qt6::Core
    Qt6::Gui
    Qt6::Widgets
)

if (TARGET Qt6::PrintSupport)
    target_link_libraries(scribble PRIVATE Qt6::PrintSupport)
endif()



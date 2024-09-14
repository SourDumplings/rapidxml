cmake_minimum_required(VERSION 3.10)

# 项目名称
project(RapidXML)

# 检查是否作为子项目
if(CMAKE_SOURCE_DIR STREQUAL PROJECT_SOURCE_DIR)
    # 作为主项目
    if(NOT CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
        set(CMAKE_INSTALL_PREFIX "${CMAKE_PREFIX_PATH}" CACHE PATH "Install path prefix" FORCE)
    else()
        set(CMAKE_INSTALL_PREFIX "${CMAKE_SOURCE_DIR}/dist" CACHE PATH "Install path prefix" FORCE)
    endif()
else()
    # 作为子项目
    if(NOT CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
        set(CMAKE_INSTALL_PREFIX "${CMAKE_PREFIX_PATH}" CACHE PATH "Install path prefix" FORCE)
    endif()
endif()

file(GLOB HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/*.hpp)

# 安装头文件
install(FILES ${HEADERS} DESTINATION include/rapidxml)
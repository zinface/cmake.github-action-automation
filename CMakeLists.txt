
cmake_minimum_required(VERSION 3.5.1)

project(cmake-github-action LANGUAGES CXX VERSION 0.0.1)

include(cmake/SparkEnvConfig.cmake)
include(cmake/SparkMacrosConfig.cmake)
include(cmake/SparkFindLibraries.cmake)
include(cmake/SparkFindQt5Config.cmake)
# include(cmake/SparkFindQt6Config.cmake)

# 资源文件路径
set(QRC_SOURCES "")

spark_add_executable_path(${PROJECT_NAME} src
    ${QRC_SOURCES}
)
target_link_qt5(${PROJECT_NAME})

include(cmake/SparkBuildGraphviz.cmake)

install(TARGETS cmake-github-action
    DESTINATION /usr/bin
)

# 注释行(使用方式)
find_package(DebPackage PATHS ${CMAKE_SOURCE_DIR})
add_package_descript(cmake/package-deb.descript)
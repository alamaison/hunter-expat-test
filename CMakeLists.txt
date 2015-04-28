
cmake_minimum_required(VERSION 2.8.11)
list(APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake)

# Package management ###########################################################

include(HunterGate)

HunterGate(
    URL "https://github.com/alamaison/hunter/archive/41aaf4df8c97174f9914c537023699e548863ee5.tar.gz"
    SHA1 "7018ac82be2606804cf27f044e0df290d9ae9caa"
)

hunter_add_package(Expat)

################################################################################

project(expat-test)

option(BUILD_SHARED_LIBS "Build Shared Libraries" ON)

add_library(foo foo.cpp)

find_package(EXPAT REQUIRED)

target_link_libraries(foo PRIVATE ${EXPAT_LIBRARIES})

target_compile_definitions(foo PRIVATE XML_STATIC)

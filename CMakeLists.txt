cmake_minimum_required(VERSION 3.6)

set(LINUX 1)
SET(BUILD_PLATFORM linux)
set(PLATFORM_FOLDER linux)
set(PLATFORM_DEFINES "-DLINUX")
add_definitions(-DUSE_CUSTOM_ENCRYPTION -pthread)

# build engine library and all tests

project(Cocos2d-x)

set(BUILD_CPP_EMPTY_TEST OFF CACHE BOOL "Build empty test samples" )
set(BUILD_CPP_TESTS OFF CACHE BOOL "Build TestCpp samples" )
set(BUILD_LUA_LIBS  OFF CACHE BOOL "Build LUA libs" )
set(BUILD_LUA_TESTS OFF CACHE BOOL "Build TestLua samples" )
set(BUILD_JS_LIBS OFF CACHE BOOL "Build js libraries" )
set(BUILD_JS_TESTS OFF CACHE BOOL "Build TestJS samples" )
set(USE_CHIPMUNK OFF CACHE BOOL "Build CHIPMUNK (physics)" )
set(USE_BULLET OFF CACHE BOOL "Build BULLET (physics)" )
set(USE_RECAST OFF CACHE BOOL "Build RECAST (physics)" )
set(USE_WEBP OFF CACHE BOOL "Build WEBP support" )
set(BUILD_EDITOR_COCOSTUDIO OFF CACHE BOOL "Build CocosStudio support" )
set(BUILD_EDITOR_SPINE OFF CACHE BOOL "Build Spine editor support" )

# cocos2dx root path
set(COCOS2DX_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/subs/cocos2d)
set(CMAKE_MODULE_PATH ${COCOS2DX_ROOT_PATH}/cmake/Modules/)

# prevent in-source-build
include(PreventInSourceBuilds)

# works before build libcocos2d
include(CocosBuildSet)

add_subdirectory(${COCOS2DX_ROOT_PATH}/cocos ${ENGINE_BINARY_PATH}/cocos/core)

# prevent tests project to build "cocos2d-x/cocos" again
set(BUILD_ENGINE_DONE ON)

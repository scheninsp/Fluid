cmake_minimum_required(VERSION 3.14)

project(main_project)

set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MD /Zi /Od /Ob0")
set(CMAKE_SHARED_LINKER_FLAGS_RELEASE "${CMAKE_SHARED_LINKER_FLAGS_RELEASE} /DEBUG /OPT:REF /OPT:ICF")

set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MD")
# remove /RTCx from default debug compile definitions
STRING (REGEX REPLACE "/RTC(su|[1su])" "" CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG}")

add_compile_definitions(_USE_MATH_DEFINES)
# could not use "#define _USE_MATH_DEFINES" in code for unknown reasons

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

# do not link directly to dll files, LNK1107 error
set (GLUT_LIB_RELEASE "D:/CppProjects/freeglut/install/lib/freeglut.lib" )
set (GLUT_LIB_DEBUG "D:/CppProjects/freeglut/install/lib/freeglutd.lib" )
set(GLUT_LIB 
    debug ${GLUT_LIB_DEBUG} optimized ${GLUT_LIB_RELEASE})
    
file(GLOB_RECURSE MAIN_PROJECT_SRC ${PROJECT_SOURCE_DIR}/src/**.cpp)
set(SOURCES ${MAIN_PROJECT_SRC})

file(GLOB_RECURSE MAIN_PROJECT_HEADERS ${PROJECT_SOURCE_DIR}/src/**.h)
source_group("Header Files" FILES ${MAIN_PROJECT_HEADERS})

include_directories(${PROJECT_SOURCE_DIR}/include)
include_directories(${PROJECT_SOURCE_DIR}/src/glvu)

add_executable(main_project ${SOURCES} ${MAIN_PROJECT_HEADERS})
set_target_properties(main_project PROPERTIES
    CXX_STANDARD 17
    PREFIX ""
    COMPILE_PDB_NAME "main_project"
)

target_link_libraries(main_project ${GLUT_LIB})

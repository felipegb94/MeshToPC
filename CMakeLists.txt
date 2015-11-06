cmake_minimum_required (VERSION 2.8)

find_package(OpenGL REQUIRED)

find_package(GLEW REQUIRED)
find_package(PkgConfig REQUIRED)
find_package(GLM REQUIRED)

pkg_search_module(GLFW REQUIRED glfw3)

include_directories(${OPENGL_INCLUDE_DIRS})

include_directories(${GLEW_INCLUDE_DIRS})
include_directories(${GLFW_INCLUDE_DIRS})
include_directories(${GLM_INCLUDE_DIRS})

include_directories(${CMAKE_CURRENT_SOURCE_DIR})


if(${OpenGL_FOUND})
    message("GLEW was found!")
    message(${GLEW_LIBRARIES})
endif()
if(${GLEW_FOUND})
    message("GLEW was found!")
    message(${GLEW_LIBRARIES})
endif()
if(${GLFW_FOUND})
    message("GLFW was found!")
    message(${GLFW_INCLUDE_DIRS})
endif()
if(${GLM_FOUND})
    message("GLM was found!")
endif()

link_directories(${GLM_LIBRARY_DIRS})
link_directories(${GLFW_LIBRARY_DIRS})

add_executable(MeshToPC MeshToPC.cpp)
target_link_libraries(MeshToPC ${OPENGL_LIBRARIES})
target_link_libraries(MeshToPC ${GLEW_LIBRARIES})
target_link_libraries(MeshToPC ${GLFW_LIBRARIES})




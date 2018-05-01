cmake_minimum_required(VERSION 2.6)

project(auto_rotation)

set(PRJ_ROOT_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../../)
set(CMAKE_MODULE_PATH ${PRJ_ROOT_DIR}/AutoFamilyPhoto/cmakes)

find_package(OPENCV REQUIRED)
find_package(SCANDIR REQUIRED)
find_package(GFLAGS REQUIRED)

add_subdirectory(${PRJ_ROOT_DIR}/FaceDetection FaceDetection.out)

include_directories(. ${PRJ_ROOT_DIR}/FaceDetection/include ${OPENCV_INCLUDE_DIR} ${SCANDIR_INCLUDE_DIR} ${GFLAGS_INCLUDE_DIR})
aux_source_directory(. SRC_LIST)

add_executable(auto_rotation ${SRC_LIST})
target_link_libraries(auto_rotation seeta_facedet_lib ${OPENCV_LIBRARIES}
    ${SCANDIR_LIBRARIES} ${GFLAGS_LIBRARIES})
    

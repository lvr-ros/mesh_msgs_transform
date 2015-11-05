cmake_minimum_required(VERSION 2.8.3)
project(mesh_msgs_transform)

find_package(catkin REQUIRED COMPONENTS
	cmake_modules
	tf
	geometry_msgs
	mesh_msgs
)

find_package(Eigen REQUIRED)

include_directories(
	include
	${catkin_INCLUDE_DIRS}
	${EIGEN_INCLUDE_DIRS}
)

link_directories(
	${catkin_LIBRARY_DIRS}
)

catkin_package(
  INCLUDE_DIRS include ${EIGEN_INCLUDE_DIRS}
  LIBRARIES mesh_msgs_transform
  CATKIN_DEPENDS tf geometry_msgs mesh_msgs 
)

add_library(mesh_msgs_transform
	src/transforms.cpp
)

target_link_libraries(mesh_msgs_transform
  ${catkin_LIBRARIES}
)

install(TARGETS mesh_msgs_transform
   DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
)

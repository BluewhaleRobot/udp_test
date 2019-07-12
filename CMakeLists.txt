cmake_minimum_required(VERSION 2.8.3)
project(udp_test)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  message_generation
)

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${PROJECT_SOURCE_DIR}/include
  ${PROJECT_SOURCE_DIR}/src
)

catkin_package(
  CATKIN_DEPENDS roscpp std_msgs message_generation message_runtime
)

add_executable(udp_node
  ${PROJECT_SOURCE_DIR}/src/udp_node.cpp
)

add_executable(udp_pub_node
  ${PROJECT_SOURCE_DIR}/src/udp_publisher.cpp
)

target_link_libraries(udp_node
  ${catkin_LIBRARIES}
)

target_link_libraries(udp_pub_node
  ${catkin_LIBRARIES}
)
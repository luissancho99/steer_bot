cmake_minimum_required(VERSION 2.8.3)
project(steer_bot_gazebo)

find_package(catkin REQUIRED COMPONENTS roscpp tf roslaunch geometry_msgs
nav_msgs gazebo_msgs)

if(${catkin_FOUND})
  catkin_package(CATKIN_DEPENDS roscpp tf geometry_msgs
  nav_msgs gazebo_msgs)
endif()

install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

if (CATKIN_ENABLE_TESTING)
    roslaunch_add_file_check(launch)
endif()

include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(groundtruth_odom_node scripts/groundtruth_odom.cpp)
target_link_libraries(groundtruth_odom_node ${catkin_LIBRARIES})

cmake_minimum_required(VERSION 3.5)

project(dummy_sensors)

if(NOT WIN32)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -Wextra -Wpedantic")
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rmw REQUIRED)
find_package(sensor_msgs REQUIRED)

add_executable(dummy_laser src/dummy_laser.cpp)
ament_target_dependencies(dummy_laser
  "rclcpp"
  "sensor_msgs")
install(TARGETS dummy_laser
  DESTINATION bin)

add_executable(dummy_joint_states src/dummy_joint_states.cpp)
ament_target_dependencies(dummy_joint_states
  "rclcpp"
  "sensor_msgs")
install(TARGETS dummy_joint_states
  DESTINATION bin)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()

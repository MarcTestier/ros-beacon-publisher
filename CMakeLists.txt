cmake_minimum_required(VERSION 3.5)
project(beacon_publisher)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

add_executable(beacon_publisher src/beacon_publisher.cpp)
ament_target_dependencies(beacon_publisher rclcpp std_msgs)

target_link_libraries(beacon_publisher bluetooth)

install(TARGETS
  beacon_publisher
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()

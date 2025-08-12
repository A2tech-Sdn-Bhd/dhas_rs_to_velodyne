cmake_minimum_required(VERSION 3.8)
project(rs_to_velodyne)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
	add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(pcl_conversions REQUIRED)
find_package(PCL REQUIRED)


add_executable(rs_to_velodyne src/rs_to_velodyne.cpp)


ament_target_dependencies(rs_to_velodyne
		rclcpp
		sensor_msgs
		pcl_conversions
)

install(
		TARGETS rs_to_velodyne
		DESTINATION lib/${PROJECT_NAME}
)


ament_package()
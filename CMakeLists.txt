cmake_minimum_required(VERSION 3.8)
project(sprayer_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
 find_package(std_msgs REQUIRED)
 find_package(rosidl_default_generators REQUIRED)

set(msg_files
  "msg/LiquidLevel.msg"
  "msg/LiquidLevelWithPercentage.msg"
  "msg/ContainerLiquidPercentage.msg"
  "msg/NozzleStatus.msg"
  "msg/NozzleStatusArray.msg"
  "msg/NozzleStatusArrayStamped.msg"
  "msg/NozzleStatusStamped.msg"
  "msg/FluidVolumetricFlowWithRate.msg"
)

set(srv_files
  "srv/SetNozzleStatus.srv"
  "srv/SetNozzleStatusArray.srv"
)

 rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  DEPENDENCIES std_msgs # Add packages that above messages depend on
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()

cmake_minimum_required(VERSION 2.8.3)
project(mscl_msgs)

find_package(catkin REQUIRED COMPONENTS message_generation std_msgs)


FILE(GLOB rosMsgFiles RELATIVE "${${PROJECT_NAME}_SOURCE_DIR}/msg"
    "${${PROJECT_NAME}_SOURCE_DIR}/msg/*.msg")

FOREACH(rosMsg ${rosMsgFiles})
    MESSAGE( STATUS "Processing message file: ${rosMsg}" )
    add_message_files( FILES ${rosMsg})
ENDFOREACH(rosMsg)

add_message_files(
  DIRECTORY msg
  FILES
  ${rosMsg}
  )

generate_messages(DEPENDENCIES std_msgs)

catkin_package(CATKIN_DEPENDS message_runtime std_msgs)

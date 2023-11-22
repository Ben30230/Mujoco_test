cmake_minimum_required(VERSION 3.5)
project(mujoco_visual)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

# if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
#   add_compile_options(-Wall -Wextra -Wpedantic)
# endif()

find_library(mujoco_lib NAME libmujoco.so.3.0.0 HINTS lib/)
message(mujoco_lib="${mujoco_lib}")

find_library(GLFW libglfw.so.3)
message(GLFW="${GLFW}")


file(GLOB_RECURSE excu_all ${CMAKE_CURRENT_SOURCE_DIR}/simulate/*.cc)
# message(excu_all="${excu_all}")

add_executable(main ${excu_all})
target_include_directories(main PRIVATE ${PROJECT_SOURCE_DIR}/include PRIVATE ${PROJECT_SOURCE_DIR}/simulate)
message(PROJECT_SOURCE_DIR="${PROJECT_SOURCE_DIR}")

target_link_libraries(main PRIVATE ${mujoco_lib} ${GLFW})




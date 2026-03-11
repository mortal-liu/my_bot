cmake_minimum_required(VERSION 3.5)
project(my_bot)

# 编译标准设置
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# 寻找依赖
find_package(ament_cmake REQUIRED)

# --- 核心修改部分：把所有安装规则放在 ament_package() 之前 ---

# 安装所有资源文件夹到 share 目录下
install(
  DIRECTORY config description launch worlds
  DESTINATION share/${PROJECT_NAME}
)

# 这一行必须在文件的最末尾！
ament_package()

cmake_minimum_required(VERSION 3.10)
project(ImGuiExample)
set(CMAKE_CXX_STANDARD 17)

# Файлы ImGui и backends
file(GLOB IMGUI_SRC
    imgui/*.cpp
    backends/imgui_impl_glfw.cpp
    backends/imgui_impl_opengl3.cpp
)

add_executable(ImGuiExample main.cpp ${IMGUI_SRC})

# Путь к GLFW и OpenGL
find_package(OpenGL REQUIRED)
find_package(glfw3 CONFIG REQUIRED)

# Пути к include
target_include_directories(ImGuiExample PRIVATE imgui backends)
target_link_libraries(ImGuiExample PRIVATE glfw OpenGL::GL)

project (Vulkan1)

cmake_minimum_required(VERSION 3.0)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS};"-g")


# sources
include_directories(${PROJECT_SOURCE_DIR})
add_executable(vulkantest 
./src/main.cpp 
./src/vke_window.cpp 
./src/first_app.cpp 
./src/vke_pipeline.cpp 
./src/vke_device.cpp 
./src/vke_swap_chain.cpp 
./src/vke_model.cpp 
./src/vke_game_object.cpp 
./src/vke_renderer.cpp 
./src/vke_simple_render_system.cpp 
./src/vke_camera.cpp 
./src/vke_buffer.cpp
./src/vke_descriptors.cpp
./src/keyboard_movement_controller.cpp
)

# Linker dependencies
target_link_libraries(vulkantest -lglfw)
target_link_libraries(vulkantest -lvulkan)
target_link_libraries(vulkantest -ldl)
target_link_libraries(vulkantest -lpthread)
target_link_libraries(vulkantest -lX11)
target_link_libraries(vulkantest -lXxf86vm)
target_link_libraries(vulkantest -lXrandr)
target_link_libraries(vulkantest -lXi)

# own dependencies
include_directories("./libs/tinyobjloader/")

# shader compilation
add_custom_target(shader_compilation ALL ../compile_shaders.sh)
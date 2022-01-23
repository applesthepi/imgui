cmake_minimum_required(VERSION 3.15)
project(imgui)

set(IMGUI_SRC
	${CMAKE_CURRENT_SOURCE_DIR}/include/imgui/imgui_demo.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/include/imgui/imgui_draw.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/include/imgui/imgui_tables.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/include/imgui/imgui_widgets.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/include/imgui/imgui.cpp

	${CMAKE_CURRENT_SOURCE_DIR}/include/backends/imgui_impl_vulkan.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/include/backends/imgui_impl_glfw.cpp
)

set(PROJECT_BINARY_DIR ${CMAKE_BINARY_DIR})
add_library(imgui STATIC
	${IMGUI_SRC}
)

target_link_libraries(imgui PUBLIC
	${Vulkan_LIBRARIES}
	#imm32.lib
	)

target_include_directories(imgui PUBLIC SYSTEM
	${PROJECT_BINARY_DIR}
	${UB_DEPENDENCIES_INCLUDE}

	${CMAKE_CURRENT_SOURCE_DIR}/include
	${CMAKE_CURRENT_SOURCE_DIR}/include/imgui
	${CMAKE_CURRENT_SOURCE_DIR}/include/backends

	${CMAKE_SOURCE_DIR}/dependencies/vulkan/Vulkan-Headers/include
	${CMAKE_SOURCE_DIR}/dependencies/vulkan/glfw/include
	${CMAKE_SOURCE_DIR}/dependencies/vulkan/glm
)

set_target_properties(imgui PROPERTIES PREFIX "lib")
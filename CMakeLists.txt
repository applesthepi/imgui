cmake_minimum_required(VERSION 3.15)
project(UB_IMGUI)

add_library(UB_IMGUI STATIC)

target_sources(UB_IMGUI PRIVATE
	"imgui_demo.cpp"
	"imgui_draw.cpp"
	"imgui_tables.cpp"
	"imgui_widgets.cpp"
	"imgui.cpp"

	"backends/imgui_impl_vulkan.cpp"
	"backends/imgui_impl_glfw.cpp"
	)

target_include_directories(UB_IMGUI PUBLIC SYSTEM
	"${CMAKE_CURRENT_SOURCE_DIR}"
	"${CMAKE_CURRENT_SOURCE_DIR}/backends"

	${Vulkan_INCLUDE_DIR}
	${CMAKE_INCLUDES}

	# TODO: fix this
	"${CMAKE_SOURCE_DIR}/vcpkg/installed/x64-windows/include"
	"${CMAKE_SOURCE_DIR}/vcpkg/installed/x64-linux/include"
	)
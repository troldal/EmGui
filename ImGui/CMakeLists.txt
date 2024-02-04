if (NOT EMSCRIPTEN)
    find_package(OpenGL REQUIRED)
    find_package(glfw3 REQUIRED)
endif ()


add_library(ImGui_Core STATIC
        imgui.cpp
        imgui_draw.cpp
        imgui_widgets.cpp
        imgui_demo.cpp imgui_tables.cpp)
target_include_directories(ImGui_Core PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
add_library(ImGui::Core ALIAS ImGui_Core)

add_library(ImGui_GLFW STATIC
        backends/imgui_impl_opengl3.cpp
        backends/imgui_impl_glfw.cpp)
target_include_directories(ImGui_GLFW PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/backends)

if (EMSCRIPTEN)
    target_link_options(ImGui_GLFW PUBLIC -sUSE_GLFW=3)
    target_link_libraries(ImGui_GLFW PUBLIC ImGui::Core glfw)
else ()
    target_link_libraries(ImGui_GLFW PUBLIC ImGui::Core glfw OpenGL::GL)
endif ()
add_library(ImGui::GLFW ALIAS ImGui_GLFW)

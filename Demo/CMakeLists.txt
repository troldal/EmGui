
if (EMSCRIPTEN)
    set(CMAKE_EXECUTABLE_SUFFIX ".html")
endif ()

add_executable(example_glfw_opengl3)
target_sources(example_glfw_opengl3 PRIVATE example_glfw_opengl3/main.cpp)
target_link_libraries(example_glfw_opengl3 PRIVATE ImGui::Core ImGui::GLFW ImGui::ImPlot)

if (EMSCRIPTEN)
    target_link_options(example_glfw_opengl3 PUBLIC -sUSE_GLFW=3 -sWASM=1 -sALLOW_MEMORY_GROWTH=1 -sNO_EXIT_RUNTIME=0 -sASSERTIONS=1)
    target_link_options(example_glfw_opengl3 PUBLIC --shell-file ${CMAKE_CURRENT_LIST_DIR}/libs/emscripten/shell_minimal.html)
    target_link_options(example_glfw_opengl3 PUBLIC --preload-file ${CMAKE_CURRENT_BINARY_DIR}/fonts/JetBrainsMono-Regular.ttf)
endif ()


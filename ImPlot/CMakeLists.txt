
add_library(ImPlot STATIC
        implot.cpp
        implot_items.cpp
        implot_demo.cpp)
target_include_directories(ImPlot PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_link_libraries(ImPlot PUBLIC ImGui::Core)
add_library(ImGui::ImPlot ALIAS ImPlot)
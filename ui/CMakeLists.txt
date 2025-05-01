add_subdirectory(dependencies)

add_executable(ui ui.cpp)

target_link_libraries(ui
  PUBLIC
    ImGui-SFML::ImGui-SFML
)

add_custom_command(
    TARGET ui POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
            "$<TARGET_FILE:ImGui-SFML>" "$<TARGET_FILE_DIR:ui>/"
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
            "$<TARGET_FILE:sfml-graphics>" "$<TARGET_FILE_DIR:ui>/"
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
            "$<TARGET_FILE:sfml-system>" "$<TARGET_FILE_DIR:ui>/"
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
            "$<TARGET_FILE:sfml-window>" "$<TARGET_FILE_DIR:ui>/"
    COMMENT "Copying target outputs to ui directory if changed"
)
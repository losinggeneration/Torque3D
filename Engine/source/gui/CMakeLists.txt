add_subdirectory(3d)
add_subdirectory(buttons)
add_subdirectory(containers)
add_subdirectory(controls)
add_subdirectory(core)
add_subdirectory(editor)
add_subdirectory(game)
add_subdirectory(shiny)
add_subdirectory(theora)
add_subdirectory(utility)
add_subdirectory(worldEditor)

link_directories(
	3d
	buttons
	containers
	controls
	core
	editor
	game
	shiny
	theora
	utility
	worldEditor
)

file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/lib.cpp)

add_library(${TORQUE_BUILD}_gui STATIC ${CMAKE_CURRENT_BINARY_DIR}/lib.cpp)
target_link_libraries(${TORQUE_BUILD}_gui LINK_INTERFACE_LIBRARIES
	${TORQUE_BUILD}_gui_3d
	${TORQUE_BUILD}_gui_buttons
	${TORQUE_BUILD}_gui_containers
	${TORQUE_BUILD}_gui_controls
	${TORQUE_BUILD}_gui_core
	${TORQUE_BUILD}_gui_editor
	${TORQUE_BUILD}_gui_game
	${TORQUE_BUILD}_gui_shiny
	${TORQUE_BUILD}_gui_theora
	${TORQUE_BUILD}_gui_utility
	${TORQUE_BUILD}_gui_worldEditor
)

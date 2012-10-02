set(TORQUE_GUI_WORLDEDITOR_SRCS
	creator.cpp
	editor.cpp
	editorIconRegistry.cpp
	editTSCtrl.cpp
	gizmo.cpp
	guiConvexShapeEditorCtrl.cpp
	guiDecalEditorCtrl.cpp
	guiMissionArea.cpp
	guiMissionAreaEditor.cpp
	guiTerrPreviewCtrl.cpp
	terrainActions.cpp
	terrainEditor.cpp
	tSelection.cpp
	undoActions.cpp
	worldEditor.cpp
	worldEditorSelection.cpp
)

set(TORQUE_GUI_WORLDEDITOR_HEADERS
	creator.h
	editor.h
	editorIconRegistry.h
	editTSCtrl.h
	gizmo.h
	guiConvexShapeEditorCtrl.h
	guiDecalEditorCtrl.h
	guiMissionAreaEditor.h
	guiMissionArea.h
	guiTerrPreviewCtrl.h
	terrainActions.h
	terrainEditor.h
	tSelection.h
	undoActions.h
	worldEditor.h
	worldEditorSelection.h
)

include_directories(
	${CMAKE_SOURCE_DIR}/../lib/tinyxml
	${CMAKE_SOURCE_DIR}/../lib/collada/include
	${CMAKE_SOURCE_DIR}/../lib/collada/include/1.4
)

add_library(${TORQUE_BUILD}_gui_worldEditor STATIC ${TORQUE_GUI_WORLDEDITOR_SRCS} ${TORQUE_GUI_WORLDEDITOR_HEADERS})
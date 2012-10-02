set(TORQUE_GUI_EDITOR_SRCS
	editorFunctions.cpp
	guiDebugger.cpp
	guiEaseViewCtrl.cpp
	guiEditCtrl.cpp
	guiFilterCtrl.cpp
	guiGraphCtrl.cpp
	guiImageList.cpp
	guiInspector.cpp
	guiInspectorTypes.cpp
	guiMenuBar.cpp
	guiParticleGraphCtrl.cpp
	guiRectHandles.cpp
	guiSeparatorCtrl.cpp
	guiShapeEdPreview.cpp
)

set(TORQUE_GUI_EDITOR_HEADERS
	editorFunctions.h
	guiDebugger.h
	guiEaseViewCtrl.h
	guiEditCtrl.h
	guiFilterCtrl.h
	guiGraphCtrl.h
	guiImageList.h
	guiInspector.h
	guiInspectorTypes.h
	guiMenuBar.h
	guiParticleGraphCtrl.h
	guiRectHandles.h
	guiSeparatorCtrl.h
	guiShapeEdPreview.h
)

include_directories(
	${CMAKE_SOURCE_DIR}/../lib/tinyxml
	${CMAKE_SOURCE_DIR}/../lib/collada/include
	${CMAKE_SOURCE_DIR}/../lib/collada/include/1.4
)

add_library(${TORQUE_BUILD}_gui_editor STATIC ${TORQUE_GUI_EDITOR_SRCS} ${TORQUE_GUI_EDITOR_HEADERS})
add_subdirectory(inspector)

add_srcs(
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

add_headers(
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

add_includes(
	${CMAKE_SOURCE_DIR}/../lib/tinyxml
	${CMAKE_SOURCE_DIR}/../lib/collada/include
	${CMAKE_SOURCE_DIR}/../lib/collada/include/1.4
)


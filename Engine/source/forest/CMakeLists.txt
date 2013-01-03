if(NOT TORQUE_DEDICATED)
add_srcs(
	editor/forestBrushElement.cpp
	editor/forestBrushTool.cpp
	editor/forestEditorCtrl.cpp
	editor/forestSelectionTool.cpp
	editor/forestTool.cpp
	editor/forestUndo.cpp
)
add_headers(
	editor/forestBrushElement.h
	editor/forestBrushTool.h
	editor/forestEditorCtrl.h
	editor/forestSelectionTool.h
	editor/forestTool.h
	editor/forestUndo.h
)
endif()

add_srcs(
	forest.cpp
	forestCell.cpp
	forestCellBatch.cpp
	forestCollision.cpp
	forestDataFile.cpp
	forestItem.cpp
	forestRender.cpp
	forestWindAccumulator.cpp
	forestWindEmitter.cpp
	forestWindMgr.cpp
	glsl/windDeformationGLSL.cpp
	hlsl/windDeformationHLSL.cpp
	ts/tsForestCellBatch.cpp
	ts/tsForestItemData.cpp
	windDeformation.cpp
)

add_headers(
	forest.h
	forestCell.h
	forestCellBatch.h
	forestCollision.h
	forestDataFile.h
	forestItem.h
	forestWindAccumulator.h
	forestWindEmitter.h
	forestWindMgr.h
	glsl/windDeformationGLSL.h
	hlsl/windDeformationHLSL.h
	ts/tsForestCellBatch.h
	ts/tsForestItemData.h
	windDeformation.h
)



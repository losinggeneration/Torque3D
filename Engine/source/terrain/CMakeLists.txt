set(TORQUE_TERRAIN_SRCS
	glsl/terrFeatureGLSL.cpp
	hlsl/terrFeatureHLSL.cpp
	terrCell.cpp
	terrCellMaterial.cpp
	terrCollision.cpp
	terrData.cpp
	terrExport.cpp
	terrFeatureTypes.cpp
	terrFile.cpp
	terrImport.cpp
	terrLighting.cpp
	terrMaterial.cpp
	terrRender.cpp
)

set(TORQUE_TERRAIN_HEADERS
	glsl/terrFeatureGLSL.h
	hlsl/terrFeatureHLSL.h
	terrCell.h
	terrCellMaterial.h
	terrCollision.h
	terrData.h
	terrFeatureTypes.h
	terrFile.h
	terrMaterial.h
	terrRender.h
)

add_library(${TORQUE_BUILD}_terrain STATIC ${TORQUE_TERRAIN_SRCS} ${TORQUE_TERRAIN_HEADERS})


set(TORQUE_LIGHTING_BASIC_SRCS
	basicLightManager.cpp
	basicSceneObjectLightingPlugin.cpp
	blInteriorSystem.cpp
	blTerrainSystem.cpp
)

set(TORQUE_LIGHTING_BASIC_HEADERS
	basicLightManager.h
	basicSceneObjectLightingPlugin.h
	blInteriorSystem.h
	blTerrainSystem.h
)

add_library(${TORQUE_BUILD}_lighting_basic STATIC
	${TORQUE_LIGHTING_BASIC_SRCS} ${TORQUE_LIGHTING_BASIC_HEADERS}
)
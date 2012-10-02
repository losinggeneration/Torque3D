set(TORQUE_LIGHTING_COMMON_SRCS
	blobShadow.cpp
	lightMapParams.cpp
	projectedShadow.cpp
	sceneLighting.cpp
	scenePersist.cpp
	shadowVolumeBSP.cpp
)

set(TORQUE_LIGHTING_COMMON_HEADERS
	blobShadow.h
	lightMapParams.h
	projectedShadow.h
	sceneLighting.h
	sceneLightingGlobals.h
	scenePersist.h
	shadowBase.h
	shadowVolumeBSP.h
)

add_library(${TORQUE_BUILD}_lighting_common STATIC
	${TORQUE_LIGHTING_COMMON_SRCS} ${TORQUE_LIGHTING_COMMON_HEADERS}
)
set(TORQUE_INTERIR_SRCS
	forceField.cpp
	interior.cpp
	interiorCollision.cpp
	interiorDebug.cpp
	interiorIO.cpp
	interiorInstance.cpp
	interiorLMManager.cpp
	interiorRender.cpp
	interiorRes.cpp
	interiorResObjects.cpp
	interiorSimpleMesh.cpp
	interiorSubObject.cpp
	mirrorSubObject.cpp
	pathedInterior.cpp
)

set(TORQUE_INTERIR_HEADERS
	forceField.h
	interior.h
	interiorInstance.h
	interiorLMManager.h
	interiorRes.h
	interiorResObjects.h
	interiorSimpleMesh.h
	interiorSubObject.h
	mirrorSubObject.h
	pathedInterior.h
)

add_library(${TORQUE_BUILD}_interior STATIC ${TORQUE_INTERIR_SRCS} ${TORQUE_INTERIR_HEADERS})


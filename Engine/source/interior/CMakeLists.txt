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

include_directories(
	${CMAKE_SOURCE_DIR}/../lib/tinyxml
	${CMAKE_SOURCE_DIR}/../lib/collada/include
	${CMAKE_SOURCE_DIR}/../lib/collada/include/1.4
)

add_library(${TORQUE_BUILD}_interior STATIC ${TORQUE_INTERIR_SRCS} ${TORQUE_INTERIR_HEADERS})


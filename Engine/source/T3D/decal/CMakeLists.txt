set(TORQUE_T3D_DECAL_SRCS
	decalData.cpp
	decalDataFile.cpp
	decalInstance.cpp
	decalManager.cpp
	decalSphere.cpp
)

set(TORQUE_T3D_DECAL_HEADERS
	decalData.h
	decalDataFile.h
	decalInstance.h
	decalManager.h
	decalSphere.h
)

add_library(${TORQUE_BUILD}_T3D_decal STATIC ${TORQUE_T3D_DECAL_SRCS} ${TORQUE_T3D_DECAL_HEADERS})
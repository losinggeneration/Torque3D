set(TORQUE_T3D_TURRET_SRCS
	aiTurretShape.cpp
	turretShape.cpp
)

set(TORQUE_T3D_TURRET_HEADERS
	aiTurretShape.h
	turretShape.h
)

add_library(${TORQUE_BUILD}_T3D_turret STATIC ${TORQUE_T3D_TURRET_SRCS} ${TORQUE_T3D_TURRET_HEADERS})
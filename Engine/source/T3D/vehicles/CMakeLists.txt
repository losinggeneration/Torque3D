set(TORQUE_T3D_VEHICLES_SRCS
	flyingVehicle.cpp
	guiSpeedometer.cpp
	hoverVehicle.cpp
	vehicle.cpp
	vehicleBlocker.cpp
	wheeledVehicle.cpp
)

set(TORQUE_T3D_VEHICLES_HEADERS
	flyingVehicle.h
	hoverVehicle.h
	vehicle.h
	vehicleBlocker.h
	wheeledVehicle.h
)

add_library(${TORQUE_BUILD}_T3D_vehicles STATIC ${TORQUE_T3D_VEHICLES_SRCS} ${TORQUE_T3D_VEHICLES_HEADERS})
set(TORQUE_T3D_FPS_SRCS
	guiClockHud.cpp
	guiCrossHairHud.cpp
	guiHealthBarHud.cpp
	guiShapeNameHud.cpp
)

add_library(${TORQUE_BUILD}_T3D_fps STATIC ${TORQUE_T3D_FPS_SRCS})
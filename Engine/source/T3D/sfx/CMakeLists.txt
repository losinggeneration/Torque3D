set(TORQUE_T3D_SFX_SRCS
	sfx3DWorld.cpp
	sfxEmitter.cpp
	sfxSpace.cpp
)

set(TORQUE_T3D_SFX_HEADERS
	sfx3DWorld.h
	sfxEmitter.h
	sfxSpace.h
)

add_library(${TORQUE_BUILD}_T3D_sfx STATIC ${TORQUE_T3D_SFX_SRCS} ${TORQUE_T3D_SFX_HEADERS})
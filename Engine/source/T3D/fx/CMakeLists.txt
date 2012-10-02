set(TORQUE_T3D_FX_SRCS
	cameraFXMgr.cpp
	explosion.cpp
	fxFoliageReplicator.cpp
	fxShapeReplicator.cpp
	groundCover.cpp
	lightning.cpp
	particle.cpp
	particleEmitter.cpp
	particleEmitterNode.cpp
	precipitation.cpp
	splash.cpp
	windEmitter.cpp
)

set(TORQUE_T3D_FX_HEADERS
	cameraFXMgr.h
	explosion.h
	fxFoliageReplicator.h
	fxShapeReplicator.h
	groundCover.h
	lightning.h
	particle.h
	particleEmitter.h
	particleEmitterNode.h
	precipitation.h
	splash.h
	windEmitter.h
)

add_library(${TORQUE_BUILD}_T3D_fx STATIC ${TORQUE_T3D_FX_SRCS} ${TORQUE_T3D_FX_HEADERS})
set(TORQUE_PHYSICS_CORE_SRCS
	physicsBody.cpp
	physicsDebris.cpp
	physicsEvents.cpp
	physicsForce.cpp
	physicsObject.cpp
	physicsPlayer.cpp
	physicsPlugin.cpp
	physicsShape.cpp
	physicsUserData.cpp
	physicsWorld.cpp
)

set(TORQUE_PHYSICS_CORE_HEADERS
	physicsBody.h
	physicsCollision.h
	physicsCommon.h
	physicsDebris.h
	physicsEvents.h
	physicsForce.h
	physicsObject.h
	physicsPlayer.h
	physicsPlugin.h
	physicsShape.h
	physicsUserData.h
	physicsWorld.h
)

if(${TORQUE_PHYSICS_BULLET})
	set(TORQUE_PHYSICS_BACKEND_SRCS
		bullet/btBody.cpp
		bullet/btCollision.cpp
		bullet/btDebugDraw.cpp
		bullet/btPlayer.cpp
		bullet/btPlugin.cpp
		bullet/btWorld.cpp
	)
	set(TORQUE_PHYSICS_BACKEND_HEADERS
		bullet/bt.h
		bullet/btBody.h
		bullet/btCasts.h
		bullet/btCollision.h
		bullet/btDebugDraw.h
		bullet/btPlayer.h
		bullet/btPlugin.h
		bullet/btWorld.h
	)

	include_directories(${CMAKE_SOURCE_DIR}/../lib/bullet/src)
elseif(${TORQUE_PHYSICS_PHYSX})
	set(TORQUE_PHYSICS_BACKEND_SRCS
		physx/pxBody.cpp
		physx/pxCloth.cpp
		physx/pxCollision.cpp
		physx/pxContactReporter.cpp
		physx/pxFluid.cpp
		physx/pxMaterial.cpp
		physx/pxMultiActor.cpp
		physx/pxPlayer.cpp
		physx/pxPlugin.cpp
		physx/pxStream.cpp
		physx/pxUtils.cpp
		physx/pxWorld.cpp
	)

	set(TORQUE_PHYSICS_BACKEND_HEADERS
		physx/px.h
		physx/pxBody.h
		physx/pxCasts.h
		physx/pxCloth.h
		physx/pxCollision.h
		physx/pxContactReporter.h
		physx/pxFluid.h
		physx/pxMaterial.h
		physx/pxMultiActor.h
		physx/pxPlayer.h
		physx/pxPlugin.h
		physx/pxStream.h
		physx/pxUtils.h
		physx/pxWorld.h
	)
else()
	# No backend physics, probably for dedicated server?
endif(${TORQUE_PHYSICS_BULLET})

add_library(${TORQUE_BUILD}_T3D_physics STATIC
	${TORQUE_PHYSICS_CORE_SRCS} ${TORQUE_PHYSICS_CORE_HEADERS}
	${TORQUE_PHYSICS_BACKEND_SRCS} ${TORQUE_PHYSICS_BACKEND_HEADERS}
)
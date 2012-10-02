set(TORQUE_T3D_GAMEBASE_SRCS
	gameBase.cpp
	gameConnection.cpp
	gameConnectionEvents.cpp
	gameProcess.cpp
	moveList.cpp
	moveManager.cpp
	processList.cpp
	tickCache.cpp
)

if(${TORQUE_GAMEBASE_STD})
	set(TORQUE_T3D_GAMEBASE_IMPL_SRCS
		std/stdGameProcess.cpp
		std/stdMoveList.cpp
	)

	set(TORQUE_T3D_GAMEBASE_IMPL_HEADERS
		std/stdGameProcess.h
		std/stdMoveList.h
	)
else()
	set(TORQUE_T3D_GAMEBASE_IMPL_SRCS
		hifi/hifiGameProcess.cpp
		hifi/hifiMoveList.cpp
	)

	set(TORQUE_T3D_GAMEBASE_IMPL_HEADERS
		hifi/hifiGameProcess.h
		hifi/hifiMoveList.h
	)
endif(${TORQUE_GAMEBASE_STD})

set(TORQUE_T3D_GAMEBASE_HEADERS
	gameBase.h
	gameConnection.h
	gameConnectionEvents.h
	gameProcess.h
	moveList.h
	moveManager.h
	processList.h
	tickCache.h
)

add_library(${TORQUE_BUILD}_T3D_gameBase STATIC
	${TORQUE_T3D_GAMEBASE_SRCS} ${TORQUE_T3D_GAMEBASE_HEADERS}
	${TORQUE_T3D_GAMEBASE_IMPL_SRCS} ${TORQUE_T3D_GAMEBASE_IMPL_HEADERS}
)
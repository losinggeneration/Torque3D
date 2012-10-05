add_srcs(
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
	add_srcs(
		std/stdGameProcess.cpp
		std/stdMoveList.cpp
	)

	add_headers(
		std/stdGameProcess.h
		std/stdMoveList.h
	)
else()
	add_srcs(
		hifi/hifiGameProcess.cpp
		hifi/hifiMoveList.cpp
	)

	add_headers(
		hifi/hifiGameProcess.h
		hifi/hifiMoveList.h
	)
endif(${TORQUE_GAMEBASE_STD})

add_headers(
	gameBase.h
	gameConnection.h
	gameConnectionEvents.h
	gameProcess.h
	moveList.h
	moveManager.h
	processList.h
	tickCache.h
)

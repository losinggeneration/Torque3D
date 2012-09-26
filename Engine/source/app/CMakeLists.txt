set(TORQUE_APP_SRCS
	badWordFilter.cpp
	banList.cpp
	game.cpp
	mainLoop.cpp
	net/httpObject.cpp
	net/net.cpp
	net/netTest.cpp
	net/serverQuery.cpp
	net/tcpObject.cpp
	version.cpp
)
set(TORQUE_APP_HEADERS
	auth.h
	badWordFilter.h
	banList.h
	game.h
	mainLoop.h
	net/httpObject.h
	net/serverQuery.h
	net/tcpObject.h
	version.h
)

add_library(${TORQUE_BUILD}_app STATIC ${TORQUE_APP_SRCS} ${TORQUE_APP_HEADERS})


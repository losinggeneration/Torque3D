set(TORQUE_APP_SRCS
	badWordFilter.cpp
	banList.cpp
	game.cpp
	mainLoop.cpp
	version.cpp
	net/httpObject.cpp
	net/net.cpp
	net/serverQuery.cpp
	net/tcpObject.cpp
)

add_library(${TORQUE_BUILD}_app STATIC ${TORQUE_APP_SRCS})
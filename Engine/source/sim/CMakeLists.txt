set(TORQUE_SIM_SRCS
	actionMap.cpp
	connectionStringTable.cpp
	netConnection.cpp
	netDownload.cpp
	netEvent.cpp
	netGhost.cpp
	netInterface.cpp
	netObject.cpp
	netStringTable.cpp
)

set(TORQUE_SIM_HEADERS
	actionMap.h
	connectionStringTable.h
	netConnection.h
	netInterface.h
	netObject.h
	netStringTable.h
)

add_library(${TORQUE_BUILD}_sim STATIC ${TORQUE_SIM_SRCS} ${TORQUE_SIM_HEADERS})


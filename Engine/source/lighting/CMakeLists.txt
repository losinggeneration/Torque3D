set(TORQUE_LIGHTING_SRCS
	lightInfo.cpp
	lightManager.cpp
	lightQuery.cpp
	lightingInterfaces.cpp
)

set(TORQUE_LIGHTING_HEADERS
	lightInfo.h
	lightManager.h
	lightQuery.h
	lightingInterfaces.h
)

add_subdirectory(advanced)
add_subdirectory(basic)
add_subdirectory(common)
add_subdirectory(shadowMap)

add_library(${TORQUE_BUILD}_lighting STATIC ${TORQUE_LIGHTING_SRCS} ${TORQUE_LIGHTING_HEADERS})

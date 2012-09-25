set(TORQUE_COMPONENT_SRCS
	componentInterface.cpp
	dynamicConsoleMethodComponent.cpp
	moreAdvancedComponent.cpp
	simComponent.cpp
	simpleComponent.cpp
)

add_library(${TORQUE_BUILD}_component STATIC ${TORQUE_COMPONENT_SRCS})
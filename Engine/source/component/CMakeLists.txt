set(TORQUE_COMPONENT_SRCS
	componentInterface.cpp
	dynamicConsoleMethodComponent.cpp
	moreAdvancedComponent.cpp
	simComponent.cpp
	simpleComponent.cpp
)
set(TORQUE_COMPONENT_HEADERS
	componentInterface.h
	dynamicConsoleMethodComponent.h
	interfaces/IProcessInput.h
	moreAdvancedComponent.h
	simComponent.h
	simpleComponent.h
)

add_library(${TORQUE_BUILD}_component STATIC ${TORQUE_COMPONENT_SRCS} ${TORQUE_COMPONENT_HEADERS})


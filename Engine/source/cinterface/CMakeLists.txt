set(TORQUE_CINTERFACE_SRCS
c_consoleInterface.cpp
c_scripting.cpp
cinterface.cpp
)

set(TORQUE_CINTERFACE_HEADERS
cinterface.h
)

add_library(${TORQUE_BUILD}_cinterface STATIC ${TORQUE_CINTERFACE_SRCS} ${TORQUE_CINTERFACE_HEADERS})

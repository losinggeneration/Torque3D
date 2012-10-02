set(TORQUE_GUI_UTILITY_SRCS
	guiBubbleTextCtrl.cpp
	guiInputCtrl.cpp
	guiMouseEventCtrl.cpp
	messageVector.cpp
)

set(TORQUE_GUI_UTILITY_HEADERS
	guiBubbleTextCtrl.h
	guiInputCtrl.h
	guiMouseEventCtrl.h
	messageVector.h
)

add_library(${TORQUE_BUILD}_gui_utility STATIC ${TORQUE_GUI_UTILITY_SRCS} ${TORQUE_GUI_UTILITY_HEADERS})
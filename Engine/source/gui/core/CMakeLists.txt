set(TORQUE_GUI_CORE_SRCS
	guiArrayCtrl.cpp
	guiCanvas.cpp
	guiControl.cpp
	guiDefaultControlRender.cpp
	guiScriptNotifyControl.cpp
	guiTypes.cpp
)

set(TORQUE_GUI_CORE_HEADERS
	guiArrayCtrl.h
	guiCanvas.h
	guiControl.h
	guiDefaultControlRender.h
	guiScriptNotifyControl.h
	guiTypes.h
)

add_library(${TORQUE_BUILD}_gui_core STATIC ${TORQUE_GUI_CORE_SRCS} ${TORQUE_GUI_CORE_HEADERS})
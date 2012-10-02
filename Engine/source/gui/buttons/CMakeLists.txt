set(TORQUE_GUI_BUTTONS_SRCS
	guiBitmapButtonCtrl.cpp
	guiBorderButton.cpp
	guiButtonBaseCtrl.cpp
	guiButtonCtrl.cpp
	guiCheckBoxCtrl.cpp
	guiIconButtonCtrl.cpp
	guiRadioCtrl.cpp
	guiSwatchButtonCtrl.cpp
	guiToggleButtonCtrl.cpp
	guiToolboxButtonCtrl.cpp
)

set(TORQUE_GUI_BUTTONS_HEADERS
	guiBitmapButtonCtrl.h
	guiButtonBaseCtrl.h
	guiButtonCtrl.h
	guiCheckBoxCtrl.h
	guiIconButtonCtrl.h
	guiRadioCtrl.h
	guiSwatchButtonCtrl.h
	guiToggleButtonCtrl.h
	guiToolboxButtonCtrl.h
)

add_library(${TORQUE_BUILD}_gui_buttons STATIC ${TORQUE_GUI_BUTTONS_SRCS} ${TORQUE_GUI_BUTTONS_HEADERS})
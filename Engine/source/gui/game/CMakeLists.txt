set(TORQUE_GUI_GAME_SRCS
	guiChunkedBitmapCtrl.cpp
	guiFadeinBitmapCtrl.cpp
	guiIdleCamFadeBitmapCtrl.cpp
	guiMessageVectorCtrl.cpp
	guiProgressBitmapCtrl.cpp
	guiProgressCtrl.cpp
)

set(TORQUE_GUI_GAME_HEADERS
	guiFadeinBitmapCtrl.h
	guiMessageVectorCtrl.h
	guiProgressBitmapCtrl.h
	guiProgressCtrl.h
)

add_library(${TORQUE_BUILD}_gui_game STATIC ${TORQUE_GUI_GAME_SRCS} ${TORQUE_GUI_GAME_HEADERS})
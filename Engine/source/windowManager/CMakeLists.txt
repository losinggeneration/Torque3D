set(TORQUE_WINDOWMANAGER_SRCS
	dedicated/dedicatedWindowStub.cpp
	platformCursorController.cpp
	platformInterface.cpp
	platformWindow.cpp
	test/testWinMgr.cpp
	win32/win32CursorController.cpp
	win32/win32SplashScreen.cpp
	win32/win32Window.cpp
	win32/win32WindowMgr.cpp
	win32/winDispatch.cpp
	windowInputGenerator.cpp
)

set(TORQUE_WINDOWMANAGER_HEADERS
	dedicated/dedicatedWindowStub.h
	mac/macCursorController.h
	mac/macView.h
	mac/macWindow.h
	mac/macWindowManager.h
	platformCursorController.h
	platformWindow.h
	platformWindowMgr.h
	win32/win32CursorController.h
	win32/win32Window.h
	win32/win32WindowMgr.h
	win32/winDispatch.h
	windowInputGenerator.h
)

add_library(${TORQUE_BUILD}_windowManager STATIC ${TORQUE_WINDOWMANAGER_SRCS} ${TORQUE_WINDOWMANAGER_HEADERS})


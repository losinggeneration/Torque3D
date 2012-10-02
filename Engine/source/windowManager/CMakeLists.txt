set(TORQUE_WINDOWMANAGER_SRCS
	platformCursorController.cpp
	platformInterface.cpp
	platformWindow.cpp
	test/testWinMgr.cpp
	windowInputGenerator.cpp
)

set(TORQUE_WINDOWMANAGER_HEADERS
	platformCursorController.h
	platformWindow.h
	platformWindowMgr.h
	windowInputGenerator.h
)

if(WIN32)
	set(TORQUE_WINDOWMANAGER_PLATFORM_SRCS
		win32/win32CursorController.cpp
		win32/win32SplashScreen.cpp
		win32/win32Window.cpp
		win32/win32WindowMgr.cpp
		win32/winDispatch.cpp
	)

	set(TORQUE_WINDOWMANAGER_PLATFORM_HEADERS
		win32/win32CursorController.h
		win32/win32Window.h
		win32/win32WindowMgr.h
		win32/winDispatch.h
	)
elseif(APPLE)
	set(TORQUE_WINDOWMANAGER_PLATFORM_SRCS
		mac/macCursorController.mm
		mac/macView.mm
		mac/macWindow.mm
		mac/macWindowManager.mm
	)

	set(TORQUE_WINDOWMANAGER_PLATFORM_HEADERS
		mac/macCursorController.h
		mac/macView.h
		mac/macWindow.h
		mac/macWindowManager.h
	)
endif()

# We actually overwrite this because it's a dedicated server
if(${TORQUE_DEDICATED})
	set(TORQUE_WINDOWMANAGER_PLATFORM_SRCS
		dedicated/dedicatedWindowStub.cpp
	)

	set(TORQUE_WINDOWMANAGER_PLATFORM_HEADERS
		dedicated/dedicatedWindowStub.h
	)
endif()

add_library(${TORQUE_BUILD}_windowManager STATIC
	${TORQUE_WINDOWMANAGER_SRCS} ${TORQUE_WINDOWMANAGER_HEADERS}
	${TORQUE_WINDOWMANAGER_PLATFORM_SRCS} ${TORQUE_WINDOWMANAGER_PLATFORM_HEADERS}
)


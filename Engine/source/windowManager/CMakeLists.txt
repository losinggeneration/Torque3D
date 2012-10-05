add_srcs(
	platformCursorController.cpp
	platformInterface.cpp
	platformWindow.cpp
	test/testWinMgr.cpp
	windowInputGenerator.cpp
)

add_headers(
	platformCursorController.h
	platformWindow.h
	platformWindowMgr.h
	windowInputGenerator.h
)

if(WIN32)
	add_srcs(
		win32/win32CursorController.cpp
		win32/win32SplashScreen.cpp
		win32/win32Window.cpp
		win32/win32WindowMgr.cpp
		win32/winDispatch.cpp
	)

	add_headers(
		win32/win32CursorController.h
		win32/win32Window.h
		win32/win32WindowMgr.h
		win32/winDispatch.h
	)
elseif(APPLE)
	add_srcs(
		mac/macCursorController.mm
		mac/macView.mm
		mac/macWindow.mm
		mac/macWindowManager.mm
	)

	add_headers(
		mac/macCursorController.h
		mac/macView.h
		mac/macWindow.h
		mac/macWindowManager.h
	)
endif()

# We actually overwrite this because it's a dedicated server
if(${TORQUE_DEDICATED})
	add_srcs(
		dedicated/dedicatedWindowStub.cpp
	)

	add_headers(
		dedicated/dedicatedWindowStub.h
	)
endif()

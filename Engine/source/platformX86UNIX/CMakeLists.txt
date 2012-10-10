add_srcs(
	threads/mutex.cpp
	threads/semaphore.cpp
	threads/thread.cpp
	x86UNIXAsmBlit.cpp
	x86UNIXCPUInfo.cpp
	x86UNIXConsole.cpp
	x86UNIXFileio.cpp
	x86UNIXIO.cpp
	x86UNIXMain.cpp
	x86UNIXMath.cpp
	x86UNIXMath_ASM.cpp
	x86UNIXMemory.cpp
	x86UNIXNet.cpp
	x86UNIXProcessControl.cpp
	x86UNIXRedbook.cpp
	x86UNIXStrings.cpp
	x86UNIXTime.cpp
	x86UNIXUtils.cpp
)

add_headers(
	platformX86UNIX.h
	x86UNIXMessageBox.h
	x86UNIXState.h
	x86UNIXStdConsole.h
	x86UNIXUtils.h
)

if(${TORQUE_DEDICATED})
	add_srcs(
		x86UNIXStub.dedicated.cpp
	)
else()
	# Client
	add_srcs(
		x86UNIXFont.client.cpp
		x86UNIXGL.client.cpp
		x86UNIXInput.client.cpp
		x86UNIXInputManager.client.cpp
		x86UNIXMessageBox.client.cpp
		x86UNIXOGLVideo.client.cpp
		x86UNIXOpenAL.client.cpp
		x86UNIXWindow.client.cpp
	)

	add_headers(
		gl_types.h
		platformAL.h
		x86UNIXFont.h
		x86UNIXInputManager.h
		x86UNIXOGLVideo.h
	)

	# Clients require freetype
	find_package(Freetype REQUIRED)

	add_includes(
		${FREETYPE_INCLUDE_DIRS}
	)

	add_libraries(
		${FREETYPE_LIBRARY}
	)
endif()

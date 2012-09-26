set(TORQUE_PLATFORMX86UNIX_SRCS
	threads/mutex.cpp
	threads/semaphore.cpp
	threads/thread.cpp
	x86UNIXAsmBlit.cpp
	x86UNIXCPUInfo.cpp
	x86UNIXConsole.cpp
	x86UNIXFileio.cpp
	x86UNIXFont.client.cpp
	x86UNIXGL.client.cpp
	x86UNIXIO.cpp
	x86UNIXInput.client.cpp
	x86UNIXInputManager.client.cpp
	x86UNIXMain.cpp
	x86UNIXMath.cpp
	x86UNIXMath_ASM.cpp
	x86UNIXMemory.cpp
	x86UNIXMessageBox.client.cpp
	x86UNIXNet.cpp
	x86UNIXOGLVideo.client.cpp
	x86UNIXOpenAL.client.cpp
	x86UNIXProcessControl.cpp
	x86UNIXRedbook.cpp
	x86UNIXStrings.cpp
	x86UNIXStub.dedicated.cpp
	x86UNIXTime.cpp
	x86UNIXUtils.cpp
	x86UNIXWindow.client.cpp
)

set(TORQUE_PLATFORMX86UNIX_HEADERS
	gl_types.h
	platformAL.h
	platformX86UNIX.h
	x86UNIXFont.h
	x86UNIXInputManager.h
	x86UNIXMessageBox.h
	x86UNIXOGLVideo.h
	x86UNIXState.h
	x86UNIXStdConsole.h
	x86UNIXUtils.h
)

add_library(${TORQUE_BUILD}_platformX86UNIX STATIC ${TORQUE_PLATFORMX86UNIX_SRCS} ${TORQUE_PLATFORMX86UNIX_HEADERS})


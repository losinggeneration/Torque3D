set(TORQUE_PLATFORM_SRCS
	async/asyncUpdate.cpp
	platform.cpp
	platformAssert.cpp
	platformCPU.cpp
	platformCPUCount.cpp
	platformCPUInfo.asm
	platformFileIO.cpp
	platformFont.cpp
	platformMemory.cpp
	platformNet.cpp
	platformNetAsync.cpp
	platformRedBook.cpp
	platformTimer.cpp
	platformVideoInfo.cpp
	platformVolume.cpp
	profiler.cpp
	threads/threadPool.cpp
)

set(TORQUE_PLATFORM_HEADERS
	async/asyncBufferedStream.h
	async/asyncPacketQueue.h
	async/asyncPacketStream.h
	async/asyncUpdate.h
	event.h
	platform.h
	platformAssert.h
	platformCPUCount.h
	platformDlibrary.h
	platformFont.h
	platformInput.h
	platformIntrinsics.gcc.h
	platformIntrinsics.h
	platformIntrinsics.visualc.h
	platformMemory.h
	platformNet.h
	platformNetAsync.h
	platformRedBook.h
	platformTLS.h
	platformTimer.h
	platformVFS.h
	platformVideoInfo.h
	platformVolume.h
	profiler.h
	threads/mutex.h
	threads/semaphore.h
	threads/thread.h
	threads/threadPool.h
	threads/threadPoolAsyncIO.h
	threads/threadSafeDeque.h
	threads/threadSafeFreeList.h
	threads/threadSafePriorityQueue.h
	threads/threadSafeRefCount.h
	tmm_off.h
	tmm_on.h
	types.codewarrior.h
	types.gcc.h
	types.h
	types.lint.h
	types.mac.h
	types.posix.h
	types.ppc.h
	types.visualc.h
	types.win32.h
	types.xenon.h
	typesLinux.h
	typesPPC.h
	typesWin32.h
	typesX86UNIX.h
	typetraits.h
)

if(!${TORQUE_DEDICATED})
	set(TORQUE_PLATFORM_CLIENT_SRCS
		menus/menuBar.cpp
		menus/popupMenu.cpp
		nativeDialogs/msgBox.cpp
		test/testAlerts.cpp
		test/testAsyncPacketQueue.cpp
		test/testBasicTypes.cpp
		test/testFile.cpp
		test/testNet.cpp
		test/testThreadPool.cpp
		test/testThreadSafeDeque.cpp
		test/testThreadSafePriorityQueue.cpp
		test/testThreadSafeRefCount.cpp
		test/testThreading.cpp
		test/testTimeManager.cpp
	)

	set(TORQUE_PLATFORM_CLIENT_HEADERS
		menus/menuBar.h
		menus/popupMenu.h
		nativeDialogs/fileDialog.h
		nativeDialogs/msgBox.h
	)
endif()

include_directories(
	${CMAKE_SOURCE_DIR}/../lib/tinyxml
)

# Not 64 bit safe...
enable_language(ASM_NASM)

set(TORQUE_PLATFORM_ASM
	platformCPUInfo.asm
)

add_library(${TORQUE_BUILD}_platform STATIC
	${TORQUE_PLATFORM_SRCS} ${TORQUE_PLATFORM_HEADERS} ${TORQUE_PLATFORM_ASM}
	${TORQUE_PLATFORM_CLIENT_SRCS} ${TORQUE_PLATFORM_CLIENT_HEADERS}
)


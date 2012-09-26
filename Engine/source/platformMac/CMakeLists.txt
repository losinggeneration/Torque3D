set(TORQUE_PLATFORMMAC_SRCS
	macCarbAsync.cpp
	macCarbCPUInfo.cpp
	macCarbFont.cpp
	macCarbInput.cpp
	macCarbMath.cpp
	macCarbMemory.cpp
	macCarbMutex.cpp
	macCarbProcessControl.cpp
	macCarbSemaphore.cpp
	macCarbStrings.cpp
	macCarbThread.cpp
	macCarbTime.cpp
	macCarbUtil.cpp
	macCarbVolume.cpp
	macDLibrary.cpp
	menus/menuBarMac.cpp
	menus/popupMenu.cpp
)

set(TORQUE_PLATFORMMAC_HEADERS
	macApplication.h
	macCarbFont.h
	macCarbVolume.h
	macGLUtils.h
	platformMacCarb.h
)

add_library(${TORQUE_BUILD}_platformMac STATIC ${TORQUE_PLATFORMMAC_SRCS} ${TORQUE_PLATFORMMAC_HEADERS})


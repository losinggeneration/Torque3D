set(TORQUE_SFX_OPENAL_SRCS
	aldlist.cpp
	sfxALBuffer.cpp
	sfxALDevice.cpp
	sfxALProvider.cpp
	sfxALVoice.cpp
)

set(TORQUE_SFX_OPENAL_HEADERS
	LoadOAL.h
	aldlist.h
	sfxALBuffer.h
	sfxALCaps.h
	sfxALDevice.h
	sfxALVoice.h
)

if(WIN32)
	set(TORQUE_SFX_OPENAL_PLATFORM_SRCS
		win32/LoadOAL.cpp
	)
elseif(APPLE)
	set(TORQUE_SFX_OPENAL_PLATFORM_SRCS
		mac/LoadOAL.mac.cpp
	)
else() # UNIX?
endif()

add_library(${TORQUE_BUILD}_sfx_openal STATIC
	${TORQUE_SFX_OPENAL_SRCS} ${TORQUE_SFX_OPENAL_HEADERS}
	${TORQUE_SFX_OPENAL_PLATFORM_SRCS}
)
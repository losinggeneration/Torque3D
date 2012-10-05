add_srcs(
	aldlist.cpp
	sfxALBuffer.cpp
	sfxALDevice.cpp
	sfxALProvider.cpp
	sfxALVoice.cpp
)

add_headers(
	LoadOAL.h
	aldlist.h
	sfxALBuffer.h
	sfxALCaps.h
	sfxALDevice.h
	sfxALVoice.h
)

if(WIN32)
	add_srcs(
		win32/LoadOAL.cpp
	)
elseif(APPLE)
	add_srcs(
		mac/LoadOAL.mac.cpp
	)
else() # UNIX?
endif()


	${TORQUE_SFX_OPENAL_SRCS} ${TORQUE_SFX_OPENAL_HEADERS}
	${TORQUE_SFX_OPENAL_PLATFORM_SRCS}
)
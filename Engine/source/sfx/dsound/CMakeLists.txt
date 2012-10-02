set(TORQUE_SFX_DSOUND_SRCS
	sfxDSBuffer.cpp
	sfxDSDevice.cpp
	sfxDSProvider.cpp
	sfxDSVoice.cpp
)

set(TORQUE_SFX_DSOUND_HEADERS
	dsFunctions.h
	sfxDSBuffer.h
	sfxDSDevice.h
	sfxDSVoice.h
)

add_library(${TORQUE_BUILD}_sfx_dsound STATIC
	${TORQUE_SFXDSOUND__SRCS} ${TORQUE_SFX_DSOUND_HEADERS}
)
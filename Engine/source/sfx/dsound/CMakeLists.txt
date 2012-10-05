add_srcs(
	sfxDSBuffer.cpp
	sfxDSDevice.cpp
	sfxDSProvider.cpp
	sfxDSVoice.cpp
)

add_headers(
	dsFunctions.h
	sfxDSBuffer.h
	sfxDSDevice.h
	sfxDSVoice.h
)


	${TORQUE_SFXDSOUND__SRCS} ${TORQUE_SFX_DSOUND_HEADERS}
)
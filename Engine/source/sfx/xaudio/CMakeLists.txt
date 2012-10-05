add_srcs(
	sfxXAudioBuffer.cpp
	sfxXAudioDevice.cpp
	sfxXAudioProvider.cpp
	sfxXAudioVoice.cpp
)

add_headers(
	sfxXAudioBuffer.h
	sfxXAudioDevice.h
	sfxXAudioVoice.h
)


	${TORQUE_SFX_XAUDIO_SRCS} ${TORQUE_SFX_XAUDIO_HEADERS}
)
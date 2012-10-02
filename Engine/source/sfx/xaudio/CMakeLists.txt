set(TORQUE_SFX_XAUDIO_SRCS
	sfxXAudioBuffer.cpp
	sfxXAudioDevice.cpp
	sfxXAudioProvider.cpp
	sfxXAudioVoice.cpp
)

set(TORQUE_SFX_XAUDIO_HEADERS
	sfxXAudioBuffer.h
	sfxXAudioDevice.h
	sfxXAudioVoice.h
)

add_library(${TORQUE_BUILD}_sfx_xaudio STATIC
	${TORQUE_SFX_XAUDIO_SRCS} ${TORQUE_SFX_XAUDIO_HEADERS}
)
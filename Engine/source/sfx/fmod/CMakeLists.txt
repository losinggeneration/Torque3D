set(TORQUE_SFX_FMOD_SRCS
	sfxFMODBuffer.cpp
	sfxFMODDevice.cpp
	sfxFMODEvent.cpp
	sfxFMODEventGroup.cpp
	sfxFMODEventSource.cpp
	sfxFMODPlugin.cpp
	sfxFMODProject.cpp
	sfxFMODProvider.cpp
	sfxFMODVoice.cpp
)

set(TORQUE_SFX_FMOD_HEADERS
	fmodErrors.h
	fmodFunctions.h
	sfxFMODBuffer.h
	sfxFMODDevice.h
	sfxFMODEvent.h
	sfxFMODEventGroup.h
	sfxFMODEventSource.h
	sfxFMODPlugin.h
	sfxFMODProject.h
	sfxFMODVoice.h
)

add_library(${TORQUE_BUILD}_sfx_fmod STATIC
	${TORQUE_SFX_FMOD_SRCS} ${TORQUE_SFX_FMOD_HEADERS}
)
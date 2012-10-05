add_srcs(
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

add_headers(
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


	${TORQUE_SFX_FMOD_SRCS} ${TORQUE_SFX_FMOD_HEADERS}
)
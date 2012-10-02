set(TORQUE_SFX_SRCS
	sfxAmbience.cpp
	sfxBuffer.cpp
	sfxController.cpp
	sfxDescription.cpp
	sfxDevice.cpp
	sfxEnvironment.cpp
	sfxFileStream.cpp
	sfxInternal.cpp
	sfxMemoryStream.cpp
	sfxModifier.cpp
	sfxParameter.cpp
	sfxPlayList.cpp
	sfxProfile.cpp
	sfxProvider.cpp
	sfxResource.cpp
	sfxSound.cpp
	sfxSoundscape.cpp
	sfxSource.cpp
	sfxState.cpp
	sfxSystem.cpp
	sfxTrack.cpp
	sfxTypes.cpp
	sfxVoice.cpp
)

set(TORQUE_SFX_HEADERS
	sfxBuffer.h
	sfxCommon.h
	sfxController.h
	sfxDescription.h
	sfxDevice.h
	sfxEnvironment.h
	sfxFileStream.h
	sfxInternal.h
	sfxMemoryStream.h
	sfxModifier.h
	sfxParameter.h
	sfxPlayList.h
	sfxProfile.h
	sfxProvider.h
	sfxResource.h
	sfxSound.h
	sfxSoundscape.h
	sfxSource.h
	sfxState.h
	sfxStream.h
	sfxSystem.h
	sfxTrack.h
	sfxTypes.h
	sfxVoice.h
	sfxWorld.h
)

if(${TORQUE_DEDICATED})
	set(TORQUE_USE_SFX_NULL 1)
endif()

if(TORQUE_USE_SFX_NULL)
	add_subdirectory(null)
	set(TORQUE_SFX_BACKEND null/${TORQUE_BUILD}_sfx_null)
elseif(TORQUE_USE_SFX_DSOUND)
	add_subdirectory(dsound)
	set(TORQUE_SFX_BACKEND null/${TORQUE_BUILD}_sfx_dsound)
elseif(TORQUE_USE_SFX_FMOD)
	add_subdirectory(fmod)
	set(TORQUE_SFX_BACKEND null/${TORQUE_BUILD}_sfx_fmod)
elseif(TORQUE_USE_SFX_OPENAL)
	add_subdirectory(openal)
	set(TORQUE_SFX_BACKEND null/${TORQUE_BUILD}_sfx_openal)
elseif(TORQUE_USE_SFX_XAUDIO)
	add_subdirectory(xaudio)
	set(TORQUE_SFX_BACKEND null/${TORQUE_BUILD}_sfx_xaudio)
endif()

add_subdirectory(media)

add_library(${TORQUE_BUILD}_sfx STATIC ${TORQUE_SFX_SRCS} ${TORQUE_SFX_HEADERS})
target_link_libraries(${TORQUE_BUILD}_sfx LINK_INTERFACE_LIBRARIES
	media/${TORQUE_BUILD}_sfx_media
	${TORQUE_SFX_BACKEND}
)


set(TORQUE_SFX_MEDIA_SRCS
	sfxVorbisStream.cpp
	sfxWavStream.cpp
)

set(TORQUE_SFX_MEDIA_HEADERS
	sfxVorbisStream.h
	sfxWavStream.h
)

add_library(${TORQUE_BUILD}_sfx_media STATIC
	${TORQUE_SFX_MEDIA_SRCS} ${TORQUE_SFX_MEDIA_HEADERS}
)
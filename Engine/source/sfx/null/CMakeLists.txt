set(TORQUE_SFX_NULL_SRCS
	sfxNullBuffer.cpp
	sfxNullDevice.cpp
	sfxNullProvider.cpp
	sfxNullVoice.cpp
)

set(TORQUE_SFX_NULL_HEADERS
	sfxNullBuffer.h
	sfxNullDevice.h
	sfxNullVoice.h
)

add_library(${TORQUE_BUILD}_sfx_null STATIC
	${TORQUE_SFX_NULL_SRCS} ${TORQUE_SFX_NULL_HEADERS}
)
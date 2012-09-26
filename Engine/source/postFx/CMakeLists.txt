set(TORQUE_POSTFX_SRCS
	postEffect.cpp
	postEffectManager.cpp
	postEffectVis.cpp
)

set(TORQUE_POSTFX_HEADERS
	postEffect.h
	postEffectCommon.h
	postEffectManager.h
	postEffectVis.h
)

add_library(${TORQUE_BUILD}_postFx STATIC ${TORQUE_POSTFX_SRCS} ${TORQUE_POSTFX_HEADERS})


set(TORQUE_LIGHTING_ADVANCED_HLSL_SRCS
	advancedLightingFeaturesHLSL.cpp
	gBufferConditionerHLSL.cpp
)

set(TORQUE_LIGHTING_ADVANCED_HLSL_HEADERS
	advancedLightingFeaturesHLSL.h
	gBufferConditionerHLSL.h
)

add_library(${TORQUE_BUILD}_lighting_advanced_hlsl STATIC
	${TORQUE_LIGHTING_ADVANCED_HLSL_SRCS} ${TORQUE_LIGHTING_ADVANCED_HLSL_HEADERS}
)
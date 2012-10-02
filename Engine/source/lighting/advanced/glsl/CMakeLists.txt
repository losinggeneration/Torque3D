set(TORQUE_LIGHTING_ADVANCED_GLSL_SRCS
	advancedLightingFeaturesGLSL.cpp
	gBufferConditionerGLSL.cpp
)

set(TORQUE_LIGHTING_ADVANCED_GLSL_HEADERS
	advancedLightingFeaturesGLSL.h
	gBufferConditionerGLSL.h
)

add_library(${TORQUE_BUILD}_lighting_advanced_glsl STATIC
	${TORQUE_LIGHTING_ADVANCED_GLSL_SRCS} ${TORQUE_LIGHTING_ADVANCED_GLSL_HEADERS}
)
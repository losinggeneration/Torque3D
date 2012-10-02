set(TORQUE_LIGHTING_ADVANCED_SRCS
	advancedLightBinManager.cpp
	advancedLightBufferConditioner.cpp
	advancedLightManager.cpp
	advancedLightingFeatures.cpp
)

set(TORQUE_LIGHTING_ADVANCED_HEADERS
	advancedLightBinManager.h
	advancedLightBufferConditioner.h
	advancedLightManager.h
	advancedLightingFeatures.h
)

if(${TORQUE_USE_GLSL})
	add_subdirectory(glsl)
elseif(${TORQUE_USE_HLSL})
	add_subdirectory(hlsl)
endif()

add_library(${TORQUE_BUILD}_lighting_advanced STATIC
	${TORQUE_LIGHTING_ADVANCED_SRCS} ${TORQUE_LIGHTING_ADVANCED_HEADERS}
)
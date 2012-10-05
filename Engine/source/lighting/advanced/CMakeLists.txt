if(${TORQUE_USE_GLSL})
	add_subdirectory(glsl)
elseif(${TORQUE_USE_HLSL})
	add_subdirectory(hlsl)
endif()

add_srcs(
	advancedLightBinManager.cpp
	advancedLightBufferConditioner.cpp
	advancedLightManager.cpp
	advancedLightingFeatures.cpp
)

add_headers(
	advancedLightBinManager.h
	advancedLightBufferConditioner.h
	advancedLightManager.h
	advancedLightingFeatures.h
)

set(TORQUE_LIGHTING_SHADOWMAP_SRCS
	cubeLightShadowMap.cpp
	dualParaboloidLightShadowMap.cpp
	lightShadowMap.cpp
	paraboloidLightShadowMap.cpp
	pssmLightShadowMap.cpp
	shadowMapManager.cpp
	shadowMapPass.cpp
	shadowMatHook.cpp
	singleLightShadowMap.cpp
)

set(TORQUE_LIGHTING_SHADOWMAP_HEADERS
	cubeLightShadowMap.h
	dualParaboloidLightShadowMap.h
	lightShadowMap.h
	paraboloidLightShadowMap.h
	pssmLightShadowMap.h
	shadowCommon.h
	shadowMapManager.h
	shadowMapPass.h
	shadowMatHook.h
	singleLightShadowMap.h
)

add_library(${TORQUE_BUILD}_lighting_shadowMap STATIC
	${TORQUE_LIGHTING_SHADOWMAP_SRCS} ${TORQUE_LIGHTING_SHADOWMAP_HEADERS}
)
set(TORQUE_MATERIALS_SRCS
	baseMatInstance.cpp
	customMaterialDefinition.cpp
	matInstance.cpp
	matInstanceHook.cpp
	matStateHint.cpp
	matTextureTarget.cpp
	materialDefinition.cpp
	materialFeatureData.cpp
	materialFeatureTypes.cpp
	materialList.cpp
	materialManager.cpp
	processedCustomMaterial.cpp
	processedFFMaterial.cpp
	processedMaterial.cpp
	processedShaderMaterial.cpp
	shaderData.cpp
	shaderMaterialParameters.cpp
)

set(TORQUE_MATERIALS_HEADERS
	baseMatInstance.h
	baseMaterialDefinition.h
	customMaterialDefinition.h
	matInstance.h
	matInstanceHook.h
	matStateHint.h
	matTextureTarget.h
	materialDefinition.h
	materialFeatureData.h
	materialFeatureTypes.h
	materialList.h
	materialManager.h
	materialParameters.h
	miscShdrDat.h
	processedCustomMaterial.h
	processedFFMaterial.h
	processedMaterial.h
	processedShaderMaterial.h
	sceneData.h
	shaderData.h
	shaderMaterialParameters.h
)

add_library(${TORQUE_BUILD}_materials STATIC ${TORQUE_MATERIALS_SRCS} ${TORQUE_MATERIALS_HEADERS})


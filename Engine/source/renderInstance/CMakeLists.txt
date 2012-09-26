set(TORQUE_RENDERINSTANCE_SRCS
	forcedMaterialMeshMgr.cpp
	renderBinManager.cpp
	renderFormatChanger.cpp
	renderGlowMgr.cpp
	renderImposterMgr.cpp
	renderMeshMgr.cpp
	renderObjectMgr.cpp
	renderOcclusionMgr.cpp
	renderParticleMgr.cpp
	renderPassManager.cpp
	renderPassStateToken.cpp
	renderPrePassMgr.cpp
	renderTerrainMgr.cpp
	renderTexTargetBinManager.cpp
	renderTranslucentMgr.cpp
)

set(TORQUE_RENDERINSTANCE_HEADERS
	forcedMaterialMeshMgr.h
	renderBinManager.h
	renderFormatChanger.h
	renderGlowMgr.h
	renderImposterMgr.h
	renderMeshMgr.h
	renderObjectMgr.h
	renderOcclusionMgr.h
	renderParticleMgr.h
	renderPassManager.h
	renderPassStateToken.h
	renderPrePassMgr.h
	renderTerrainMgr.h
	renderTexTargetBinManager.h
	renderTranslucentMgr.h
)

add_library(${TORQUE_BUILD}_renderInstance STATIC ${TORQUE_RENDERINSTANCE_SRCS} ${TORQUE_RENDERINSTANCE_HEADERS})


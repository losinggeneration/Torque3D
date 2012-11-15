set(CONVEXDECOMP_SRCS
	NvConcavityVolume.cpp
	NvConvexDecomposition.cpp
	NvFloatMath.cpp
	NvMeshIslandGeneration.cpp
	NvRayCast.cpp
	NvRemoveTjunctions.cpp
	NvSplitMesh.cpp
	NvStanHull.cpp
	NvThreadConfig.cpp
	wavefront.cpp
)

set(CONVEXDECOMP_HEADERS
	NvConcavityVolume.h
	NvConvexDecomposition.h
	NvFloatMath.h
	NvHashMap.h
	NvMeshIslandGeneration.h
	NvRayCast.h
	NvRemoveTjunctions.h
	NvSimpleTypes.h
	NvSplitMesh.h
	NvStanHull.h
	NvThreadConfig.h
	NvUserMemAlloc.h
	wavefront.h
)

add_library(convexdecomp STATIC ${CONVEXDECOMP_SRCS} ${CONVEXDECOMP_HEADERS})

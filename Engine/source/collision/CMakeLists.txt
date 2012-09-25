set(TORQUE_COLLISION_SRCS
	abstractPolyList.cpp
	boxConvex.cpp
	clippedPolyList.cpp
	concretePolyList.cpp
	convex.cpp
	depthSortList.cpp
	earlyOutPolyList.cpp
	extrudedPolyList.cpp
	gjk.cpp
	optimizedPolyList.cpp
	planeExtractor.cpp
	polytope.cpp
	vertexPolyList.cpp
)

add_library(${TORQUE_BUILD}_collision STATIC ${TORQUE_COLLISION_SRCS})
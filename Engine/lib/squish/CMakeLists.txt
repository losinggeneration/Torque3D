set(SQUISH_SRCS
	alpha.cpp
	clusterfit.cpp
	colourblock.cpp
	colourfit.cpp
	colourset.cpp
	maths.cpp
	rangefit.cpp
	singlecolourfit.cpp
	squish.cpp
	squishMath.cpp
	squishOmp.cpp
)

set(SQUISH_HEADERS
	alpha.h
	clusterfit.h
	colourblock.h
	colourfit.h
	colourset.h
	config.h
	maths.h
	rangefit.h
	simd.h
	simd_float.h
	simd_sse.h
	simd_ve.h
	singlecolourfit.h
	squish.h
	squishMath.h
)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}
)

add_library(squish STATIC ${SQUISH_SRCS} ${SQUISH_HEADERS})

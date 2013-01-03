set(LIBOGG_SRCS
	src/framing.c
	src/bitwise.c
)

set(LIBOGG_HEADERS
	include/ogg/ogg.h
	include/ogg/os_types.h
)

include_directories(include)

add_library(ogg STATIC ${LIBOGG_SRCS} ${LIBOGG_HEADERS})

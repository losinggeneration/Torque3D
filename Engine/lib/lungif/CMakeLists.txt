set(LUNGIF_SRCS
	dgif_lib.c
	gif_err.c
	gifalloc.c
)

set(LUNGIF_HEADERS
	gif_lib.h
	gif_lib_private.h
)

if(UNIX OR APPLE)
	add_definitions(-DHAVE_FCNTL_H -DHAVE_UNISTD_H)
elseif(WIN32)
	add_definitions(-DHAVE_IO_H)
endif()

add_library(ungif STATIC ${LUNGIF_SRCS} ${LUNGIF_HEADERS})

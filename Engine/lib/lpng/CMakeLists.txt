set(PNG_SRCS
	png.c
	pngerror.c
	pnggccrd.c
	pngget.c
	pngmem.c
	pngpread.c
	pngread.c
	pngrio.c
	pngrtran.c
	pngrutil.c
	pngset.c
	pngtrans.c
	pngvcrd.c
	pngwio.c
	pngwrite.c
	pngwtran.c
	pngwutil.c
)

set(PNG_HEADERS
	pngasmrd.h
	pngconf.h
	png.h
)

add_library(png STATIC ${PNG_SRCS} ${PNG_HEADERS})

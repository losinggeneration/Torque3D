set(LIBTHEORA_SRCS
	lib/enc/encoder_toplevel.c
	lib/enc/misc_common.c
	lib/enc/pp.c
	lib/enc/encoder_quant.c
	lib/enc/encoder_idct.c
	lib/enc/encapiwrapper.c
	lib/enc/frarray.c
	lib/enc/encoder_huffman.c
	lib/enc/reconstruct.c
	lib/enc/blockmap.c
	lib/enc/dct_decode.c
	lib/enc/frinit.c
	lib/enc/dct.c
	lib/enc/scan.c
	lib/enc/mcomp.c
	lib/enc/pb.c
	lib/enc/dct_encode.c
	lib/enc/dsp.c
	lib/enc/encode.c
	lib/cpu.c
	lib/dec/idct.c
	lib/dec/decinfo.c
	lib/dec/huffdec.c
	lib/dec/info.c
	lib/dec/internal.c
	lib/dec/state.c
	lib/dec/dequant.c
	lib/dec/decapiwrapper.c
	lib/dec/fragment.c
	lib/dec/bitpack.c
	lib/dec/decode.c
	lib/dec/quant.c
	lib/dec/apiwrapper.c
)

# TODO: Figure out what actually needs included for MMX
if(0)

list(APPEND LIBTHEORA_SRCS
	lib/dec/x86/mmxfrag.c
	lib/dec/x86/x86state.c
	lib/dec/x86/mmxidct.c
	lib/dec/x86/mmxstate.c
)

list(APPEND LIBTHEORA_SRCS
	lib/dec/x86_vc/mmxfrag.c
	lib/dec/x86_vc/x86state.c
	lib/dec/x86_vc/mmxidct.c
	lib/dec/x86_vc/mmxloopfilter.c
	lib/dec/x86_vc/mmxstate.c
)

if(${CMAKE_SIZEOF_VOID_P} EQUAL 4)
	list(APPEND LIBTHEORA_SRCS
		lib/enc/x86_32_vs/dsp_mmx.c
		lib/enc/x86_32_vs/recon_mmx.c
		lib/enc/x86_32_vs/fdct_mmx.c
		lib/enc/x86_32/dct_decode_mmx.c
		lib/enc/x86_32/idct_mmx.c
		lib/enc/x86_32/dsp_mmx.c
		lib/enc/x86_32/recon_mmx.c
		lib/enc/x86_32/dsp_mmxext.c
		lib/enc/x86_32/fdct_mmx.c
	)
else()
	list(APPEND LIBTHEORA_SRCS
		lib/enc/x86_64/dct_decode_mmx.c
		lib/enc/x86_64/idct_mmx.c
		lib/enc/x86_64/dsp_mmx.c
		lib/enc/x86_64/recon_mmx.c
		lib/enc/x86_64/dsp_mmxext.c
		lib/enc/x86_64/fdct_mmx.c
	)
endif()
endif()

set(LIBTHEORA_HEADERS
	include/theora/theoradec.h
	include/theora/codec.h
	include/theora/theora.h
	include/theora/theoraenc.h
	lib/cpu.h
	lib/enc/toplevel_lookup.h
	lib/enc/encoder_huffman.h
	lib/enc/block_inline.h
	lib/enc/encoder_lookup.h
	lib/enc/pp.h
	lib/enc/quant_lookup.h
	lib/enc/dsp.h
	lib/enc/hufftables.h
	lib/enc/codec_internal.h
	lib/dec/dct.h
	lib/dec/bitpack.h
	lib/dec/quant.h
	lib/dec/decint.h
	lib/dec/idct.h
	lib/dec/x86/x86int.h
	lib/dec/dequant.h
	lib/dec/huffdec.h
	lib/dec/huffman.h
	lib/dec/ocintrin.h
	lib/dec/apiwrapper.h
	lib/dec/x86_vc/x86int.h
	lib/internal.h
)

include_directories(include)

add_library(theora STATIC ${LIBTHEORA_SRCS} ${LIBTHEORA_HEADERS})

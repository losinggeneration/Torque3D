set(PCRE_SRCS
	pcre_chartables.c
	pcre_compile.c
	pcre_config.c
	pcrecpp.cc
	pcre_dfa_exec.c
	pcre_exec.c
	pcre_fullinfo.c
	pcre_get.c
	pcre_globals.c
	pcre_info.c
	pcre_maketables.c
	pcre_newline.c
	pcre_ord2utf8.c
	pcre_refcount.c
	pcre_scanner.cc
	pcre_stringpiece.cc
	pcre_study.c
	pcre_tables.c
	pcre_try_flipped.c
	pcre_ucp_searchfuncs.c
	pcre_valid_utf8.c
	pcre_version.c
	pcre_xclass.c
)

set(PCRE_HEADERS
	config.h
	pcrecpparg.h
	pcrecpp.h
	pcrecpp_internal.h
	pcre.h
	pcre_internal.h
	pcreposix.h
	pcre_scanner.h
	pcre_stringpiece.h
	ucp.h
	ucpinternal.h
	ucptable.h
)

add_definitions(-DPCRE_STATIC -DHAVE_CONFIG_H)

add_library(pcre STATIC ${PCRE_SRCS} ${PCRE_HEADERS})

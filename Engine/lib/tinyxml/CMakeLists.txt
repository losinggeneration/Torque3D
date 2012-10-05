set(TINYXML_SRCS
	tinystr.cpp
	tinyxml.cpp
	tinyxmlerror.cpp
	tinyxmlparser.cpp
)

set(TINYXML_HEADERS
	tinystr.h
	tinyxml.h
)

add_library(tinyxml STATIC ${TINYXML_SRCS} ${TINYXML_HEADERS})

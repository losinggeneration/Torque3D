set(TORQUE_i18n_SRCS
	i18n.cpp
	lang.cpp
)

set(TORQUE_i18n_HEADERS
	i18n.h
	lang.h
)

add_library(${TORQUE_BUILD}_i18n STATIC ${TORQUE_i18n_SRCS} ${TORQUE_i18n_HEADERS})


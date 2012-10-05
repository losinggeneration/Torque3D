add_subdirectory(advanced)
add_subdirectory(basic)
add_subdirectory(common)
add_subdirectory(shadowMap)

add_srcs(
	lightInfo.cpp
	lightManager.cpp
	lightQuery.cpp
	lightingInterfaces.cpp
	shadowManager.cpp
)

add_headers(
	lightInfo.h
	lightManager.h
	lightQuery.h
	lightingInterfaces.h
	shadowManager.h
)

project(Torque3D)
cmake_minimum_required(VERSION 2.8)

# Treat link_directories as relative to CMAKE_CURRENT_SOURCE_DIR
cmake_policy(SET CMP0015 NEW)

# Select the defalt physics engine to use
option(TORQUE_PHYSICS_BULLET "Build Torque with Bullet for it's physics" ON)
option(TORQUE_PHYSICS_PHYSX "Build Torque with PhysX for it's physics" OFF)
if(TORQUE_PHYSICS_BULLET AND TORQUE_PHYSICS_PHYSX)
	message(FATAL_ERROR "Only one physics option can be chosen")
endif()

# Select the defalt shader language to use
option(TORQUE_USE_GLSL "Use GLSL as the default shader language" ON)
option(TORQUE_USE_HLSL "Use HLSL as the default shader language" OFF)
if(TORQUE_USE_GLSL AND TORQUE_USE_HLSL)
	message(FATAL_ERROR "Only one shader language option can be chosen")
endif()

# Select the defalt gameBase to use
option(TORQUE_GAMEBASE_STD "Use gameBase/std" ON)
option(TORQUE_GAMEBASE_HIFI "Use gameBase/hifi" OFF)
if(TORQUE_GAMEBASE_STD AND TORQUE_GAMEBASE_HIFI)
	message(FATAL_ERROR "Only one gamebase option can be chosen")
endif()

option(TORQUE_DEDICATED "Build Torque dedicated server" OFF)
set(TORQUE_BUILD "Full" CACHE STRING "The Application's name")

# TODO option: TORQUE_USE_SFX_DSOUND
# TODO option: TORQUE_USE_SFX_FMOD
# TODO option: TORQUE_USE_SFX_NULL
# TODO option: TORQUE_USE_SFX_OPENAL
# TODO option: TORQUE_USE_SFX_XAUDIO
# TODO option: To use dynamic or static linking

if(${TORQUE_DEDICATED})
	add_definitions(-DTORQUE_DEDICATED)
	# We want to unset any extra physics
	unset(TORQUE_PHYSICS_BULLET)
	unset(TORQUE_PHYSICS_PHYSX)
	set(TORQUE_BUILD_TARGET ${TORQUE_BUILD})
else()
	set(TORQUE_BUILD_TARGET ${TORQUE_BULID}_Shared)
endif(${TORQUE_DEDICATED})

# This is to help set where executables should be written
if(${CMAKE_GENERATOR} MATCHES "Visual Studio 10")
	set(BUILD_TARGET "Visual Studio 2010")
elseif(${CMAKE_GENERATOR} MATCHES "Visual Studio 9")
	set(BUILD_TARGET "Visual Studio 2008")
elseif(${CMAKE_GENERATOR} MATCHES Makefiles)
	if(${TORQUE_DEDICATED})
		set(BUILD_TARGET "Make_Ded")
	else()
		set(BUILD_TARGET "Make")
	endif()
else()
	set(BUILD_TARGET ${CMAKE_GENERATOR})
endif()

# set(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/../../Templates/${TORQUE_BUILD}/buildFiles/${BUILD_TARGET}/)

include_directories(
	# Needed for torqueConfig.h
	${CMAKE_SOURCE_DIR}
	${CMAKE_CURRENT_SOURCE_DIR}/../lib/
	${CMAKE_CURRENT_BINARY_DIR}
)

set(TORQUE_ENGINE_PRODUCT 0006)
set(TORQUE_APP_NAME ${TORQUE_BUILD})
set(TORQUE_APP_VERSION 2009)
set(TORQUE_APP_VERSION_STRING  "2009")
set(TORQUE_MULTITHREAD TRUE)
set(TORQUE_DISABLE_MEMORY_MANAGER TRUE)
set(TORQUE_DISABLE_VIRTUAL_MOUNT_SYSTEM FALSE)
set(TORQUE_DISABLE_FIND_ROOT_WITHIN_ZIP FALSE)

configure_file(cmake/torqueConfig.h.in torqueConfig.h)

macro(add_srcs)
	file(RELATIVE_PATH _relative_path "${CMAKE_SOURCE_DIR}" "${CMAKE_CURRENT_SOURCE_DIR}")

	foreach(_srcs ${ARGN})
		list(APPEND TORQUE_ENGINE_SRCS "${_relative_path}/${_srcs}")
	endforeach()

	if(_relative_path)
		set(TORQUE_ENGINE_SRCS ${TORQUE_ENGINE_SRCS} PARENT_SCOPE)
	endif()
endmacro(add_srcs)

macro(add_headers)
	file(RELATIVE_PATH _relative_path "${CMAKE_SOURCE_DIR}" "${CMAKE_CURRENT_SOURCE_DIR}")

	foreach(_headers ${ARGN})
		list(APPEND TORQUE_ENGINE_HEADERS "${_relative_path}/${_headers}")
	endforeach()

	if(_relative_path)
		set(TORQUE_ENGINE_HEADERS ${TORQUE_ENGINE_HEADERS} PARENT_SCOPE)
	endif()
endmacro(add_headers)

macro(add_includes)
	file(RELATIVE_PATH _relative_path "${CMAKE_SOURCE_DIR}" "${CMAKE_CURRENT_SOURCE_DIR}")

	foreach(_includes ${ARGN})
		list(APPEND TORQUE_ENGINE_INCLUDES "${_includes}")
	endforeach()

	if(_relative_path)
		set(TORQUE_ENGINE_INCLUDES ${TORQUE_ENGINE_INCLUDES} PARENT_SCOPE)
	endif()
endmacro(add_includes)

macro(add_libraries)
	file(RELATIVE_PATH _relative_path "${CMAKE_SOURCE_DIR}" "${CMAKE_CURRENT_SOURCE_DIR}")

	foreach(_libraries ${ARGN})
		list(APPEND TORQUE_ENGINE_LIBRARIES "${_libraries}")
	endforeach()

	if(_relative_path)
		set(TORQUE_ENGINE_LIBRARIES ${TORQUE_ENGINE_LIBRARIES} PARENT_SCOPE)
	endif()
endmacro(add_libraries)

# Not 64 bit safe...
enable_language(ASM_NASM)

# Some generic options to include by default for now
add_definitions(
	-DUNICODE
	-DTORQUE_SHADERGEN
	-DTORQUE_UNICODE
	-DBAN_OPCODE_AUTOLINK
	-DICE_NO_DLL
	-DTORQUE_OPCODE
	-DTORQUE_ADVANCED_LIGHTING
	-DTORQUE_BASIC_LIGHTING
	-DTORQUE_OGGVORBIS
	-DTORQUE_OGGTHEORA
	-DTORQUE_COLLADA
	-DDOM_INCLUDE_TINYXML
	-DPCRE_STATIC
)

if(CMAKE_COMPILER_IS_GNUCC OR CMAKE_COMPILER_IS_GNUCXX)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -mmmx -msse")
	if(${CMAKE_SIZEOF_VOID_P} EQUAL 8)
		add_definitions(-Di386)
		set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -m32")
		set(LINK_FLAGS "-m32")
	endif()
endif()

if(UNIX)
	add_definitions(-DLINUX)

	find_package(SDL REQUIRED)
	include_directories(${SDL_INCLUDE_DIRS})

	add_subdirectory(platformPOSIX)
	add_subdirectory(platformX86UNIX)
elseif(APPLE)
	add_subdirectory(platformPOSIX)
	add_subdirectory(platformMac)
elseif(WIN32)
	add_subdirectory(platformWin32)
else()
	message(FATAL_ERROR "Unknown Platform")
endif(UNIX)

if(!${TORQUE_DEDICATED})
	add_subdirectory(main)
endif()

add_subdirectory(T3D)
add_subdirectory(app)
add_subdirectory(cinterface)
add_subdirectory(collision)
add_subdirectory(component)
add_subdirectory(console)
add_subdirectory(core)
add_subdirectory(environment)
add_subdirectory(forest)
add_subdirectory(gfx)
add_subdirectory(gui)
add_subdirectory(i18n)
add_subdirectory(interior)
add_subdirectory(lighting)
add_subdirectory(materials)
add_subdirectory(math)
add_subdirectory(platform)
add_subdirectory(postFx)
add_subdirectory(renderInstance)
add_subdirectory(scene)
add_subdirectory(sfx)
add_subdirectory(shaderGen)
add_subdirectory(sim)
add_subdirectory(terrain)
add_subdirectory(ts)
add_subdirectory(unit)
add_subdirectory(util)
add_subdirectory(windowManager)

add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/bullet ${CMAKE_CURRENT_BINARY_DIR}/bullet)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/collada ${CMAKE_CURRENT_BINARY_DIR}/collada)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/convexDecomp ${CMAKE_CURRENT_BINARY_DIR}/convexDecomp)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/libogg ${CMAKE_CURRENT_BINARY_DIR}/libogg)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/libvorbis ${CMAKE_CURRENT_BINARY_DIR}/libvorbis)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/ljpeg ${CMAKE_CURRENT_BINARY_DIR}/ljpeg)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/lmng ${CMAKE_CURRENT_BINARY_DIR}/lmng)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/lpng ${CMAKE_CURRENT_BINARY_DIR}/lpng)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/lungif ${CMAKE_CURRENT_BINARY_DIR}/lungif)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/opcode ${CMAKE_CURRENT_BINARY_DIR}/opcode)
#add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/openal ${CMAKE_CURRENT_BINARY_DIR}/openal)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/pcre ${CMAKE_CURRENT_BINARY_DIR}/pcre)
#add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/sdl ${CMAKE_CURRENT_BINARY_DIR}/sdl)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/squish ${CMAKE_CURRENT_BINARY_DIR}/squish)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/tinyxml ${CMAKE_CURRENT_BINARY_DIR}/tinyxml)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/zlib ${CMAKE_CURRENT_BINARY_DIR}/zlib)

set(BULLET_TARGETS BulletDynamics BulletSoftBody BulletCollision LinearMath)

include_directories(
	${TORQUE_ENGINE_INCLUDES}
)


if(${TORQUE_DEDICATED})
	add_executable(${TORQUE_BUILD_TARGET} main/main.cpp ${TORQUE_ENGINE_SRCS} ${TORQUE_ENGINE_HEADERS})
else()
	add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/libtheora ${CMAKE_CURRENT_BINARY_DIR}/libtheora)

	add_executable(${TORQUE_BUILD_TARGET} main/main.cpp)
	add_library(${TORQUE_BUILD}_engine SHARED ${TORQUE_ENGINE_SRCS} ${TORQUE_ENGINE_HEADERS})
	set(TORQUE_ENGINE ${TORQUE_BUILD}_engine)

	target_link_libraries(${TORQUE_BUILD_TARGET}
		theora
	)
endif()

target_link_libraries(${TORQUE_BUILD_TARGET}
	${TORQUE_ENGINE}
	${BULLET_TARGETS}
	collada
	convexdecomp
	rt # for convexDecomp and Linux
	opcode
	pcre
	jpeg
	png
	ungif
	squish
	tinyxml
	z
	vorbis
	ogg
	mng
	${SDL_LIBRARY}
# TODO: Check if this needs to happen at the shared library level instead of the main executable target level
	${TORQUE_ENGINE_LIBRARIES}
)

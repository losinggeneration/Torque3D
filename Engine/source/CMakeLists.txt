project(Torque3D)
cmake_minimum_required(VERSION 2.8)

# Treat link_directories as relative to CMAKE_CURRENT_SOURCE_DIR
cmake_policy(SET CMP0015 NEW)

include(CMakeDependentOption)
# We can only choose one build type
CMAKE_DEPENDENT_OPTION(TORQUE_FULL_BUILD "Set the Torque3D to the Full build" OFF
	"NOT TORQUE_FULL_PHYSX_BUILD; NOT TORQUE_EMPTY_BUILD; NOT TORQUE_EMPTY_PHYSX_BUILD" OFF)

CMAKE_DEPENDENT_OPTION(TORQUE_FULL_PHYSX_BUILD "Set the Torque3D to the Full PhysX build" OFF
	"NOT TORQUE_FULL_BUILD; NOT TORQUE_EMPTY_BUILD; NOT TORQUE_EMPTY_PHYSX_BUILD" OFF)

CMAKE_DEPENDENT_OPTION(TORQUE_EMPTY_BUILD "Set the Torque3D to the Empty build" OFF
	"NOT TORQUE_FULL_BUILD; NOT TORQUE_FULL_PHYSX_BUILD; NOT TORQUE_EMPTY_PHYSX_BUILD" OFF)

CMAKE_DEPENDENT_OPTION(TORQUE_EMPTY_PHYSX_BUILD "Set the Torque3D to the Empty PhysX build" OFF
	"NOT TORQUE_FULL_BUILD; NOT TORQUE_FULL_PHYSX_BUILD; NOT TORQUE_EMPTY_BUILD" OFF)

# Select the defalt shader language to use
CMAKE_DEPENDENT_OPTION(TORQUE_USE_GLSL "Use GLSL as the default shader language" OFF
	"NOT TORQUE_USE_HLSL" OFF)
CMAKE_DEPENDENT_OPTION(TORQUE_USE_HLSL "Use HLSL as the default shader language" OFF
	"NOT TORQUE_USE_GLSL" OFF)

option(TORQUE_DEDICATED "Build Torque dedicated server" OFF)
# TODO Option for T3D/gameBase/ std or hifi
# TODO option: TORQUE_USE_SFX_DSOUND
# TODO option: TORQUE_USE_SFX_FMOD
# TODO option: TORQUE_USE_SFX_NULL
# TODO option: TORQUE_USE_SFX_OPENAL
# TODO option: TORQUE_USE_SFX_XAUDIO

# Set some options based on the build type
if(${TORQUE_FULL_BUILD})
	set(TORQUE_BUILD "Full")
	set(TORQUE_PHYSICS_BULLET 1)
elseif(${TORQUE_FULL_PHYSX_BUILD})
	set(TORQUE_BUILD "Full_PhysX")
	set(TORQUE_PHYSICS_PHYSX 1)
elseif(${TORQUE_EMPTY_BUILD})
	set(TORQUE_BUILD "Empty")
	set(TORQUE_PHYSICS_BULLET 1)
elseif(${TORQUE_EMPTY_PHYSX_BUILD})
	set(TORQUE_BUILD "Empty_PhysX")
	set(TORQUE_PHYSICS_PHYSX 1)
else()
	message(FATAL_ERROR "No build selected")
endif(${TORQUE_FULL_BUILD})

if(${TORQUE_DEDICATED})
	add_definitions(-DTORQUE_DEDICATED)
	# We want to unset any extra physics
	set(TORQUE_PHYSICS_BULLET 0)
	set(TORQUE_PHYSICS_PHYSX 0)
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

if(${UNIX})
	add_definitions(-DLINUX)
endif(${UNIX})

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

configure_file(cmake/torqueConfig.h.in torqueConfig.h)

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

if(UNIX)
	find_library(SDL REQUIRED)
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

add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/squish ${CMAKE_CURRENT_BINARY_DIR}/squish)

link_directories(
	T3D
	app
	cinterface
	collision
	component
	console
	core
	environment
	forest
	gfx
	gui
	i18n
	interior
	lighting
	main
	materials
	math
	platform
	postFx
	renderInstance
	scene
	sfx
	shaderGen
	sim
	terrain
	ts
	unit
	util
	windowManager
)

if(${TORQUE_DEDICATED})
	add_executable(${TORQUE_BUILD_TARGET} main/main.cpp)
else()
	file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/lib.cpp)
	add_library(${TORQUE_BUILD_TARGET} SHARED ${CMAKE_CURRENT_BINARY_DIR}/lib.cpp)
endif()

if(UNIX)
	link_directories(
		platformPOSIX
		platformX86UNIX
	)

	set(TORQUE_PLATFORM_LIBS
		${TORQUE_BUILD}_platformX86UNIX
		${TORQUE_BUILD}_platformPOSIX
		${SDL_LIBRARY}
		SDL
	)
elseif(APPLE)
	link_directories(
		platformMac
	)

	target_link_libraries(${TORQUE_BUILD}
		${TORQUE_BUILD}_platformMac
	)
elseif(WIN32)
	link_directories(
		platformWin32
	)

	target_link_libraries(${TORQUE_BUILD_TARGET}
		${TORQUE_BUILD}_platformWin32
	)
endif()

target_link_libraries(${TORQUE_BUILD_TARGET}
	${TORQUE_BUILD}_T3D
	${TORQUE_BUILD}_collision
	${TORQUE_BUILD}_component
	${TORQUE_BUILD}_gui
	${TORQUE_BUILD}_app
	${TORQUE_BUILD}_console
	${TORQUE_BUILD}_util
	${TORQUE_PLATFORM_LIBS}
	${TORQUE_BUILD}_gfx
	${TORQUE_BUILD}_app
	${TORQUE_BUILD}_sfx
	${TORQUE_BUILD}_sfx_media
	${TORQUE_BUILD}_math
	${TORQUE_BUILD}_cinterface
	${TORQUE_BUILD}_console
	${TORQUE_BUILD}_T3D
	${TORQUE_BUILD}_enviornment
	${TORQUE_BUILD}_forest
	${TORQUE_BUILD}_i18n
	${TORQUE_BUILD}_interior
	${TORQUE_BUILD}_lighting
	${TORQUE_BUILD}_materials
	${TORQUE_BUILD}_platform
	${TORQUE_BUILD}_sim
	${TORQUE_BUILD}_core
	${TORQUE_BUILD}_postFx
	${TORQUE_BUILD}_renderInstance
	${TORQUE_BUILD}_scene
	${TORQUE_BUILD}_shaderGen
	${TORQUE_BUILD}_terrain
	${TORQUE_BUILD}_ts
	${TORQUE_BUILD}_unit
	${TORQUE_BUILD}_windowManager
	squish
	z
	vorbisfile
)

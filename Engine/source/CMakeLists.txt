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
# TODO option: To use dynamic or static linking

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

add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/collada ${CMAKE_CURRENT_BINARY_DIR}/collada)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/opcode ${CMAKE_CURRENT_BINARY_DIR}/opcode)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/pcre ${CMAKE_CURRENT_BINARY_DIR}/pcre)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/lpng ${CMAKE_CURRENT_BINARY_DIR}/lpng)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/squish ${CMAKE_CURRENT_BINARY_DIR}/squish)
add_subdirectory(${CMAKE_SOURCE_DIR}/../lib/tinyxml ${CMAKE_CURRENT_BINARY_DIR}/tinyxml)

include_directories(
	${TORQUE_ENGINE_INCLUDES}
)


if(${TORQUE_DEDICATED})
	add_executable(${TORQUE_BUILD_TARGET} main/main.cpp)

	add_library(${TORQUE_BUILD}_engine STATIC ${TORQUE_ENGINE_SRCS} ${TORQUE_ENGINE_HEADERS})
else()
	file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/lib.cpp)

	add_executable(${TORQUE_BUILD_TARGET} main/main.cpp)
	add_library(${TORQUE_BUILD}_engine SHARED ${TORQUE_ENGINE_SRCS} ${TORQUE_ENGINE_HEADERS})
endif()

target_link_libraries(${TORQUE_BUILD_TARGET}
	${TORQUE_BUILD}_engine
	collada
	opcode
	pcre
	png
	squish
	tinyxml
	z
	vorbisfile
	${SDL_LIBRARY}
# TODO: Check if this needs to happen at the shared library level instead of the main executable target level
	${TORQUE_ENGINE_LIBRARIES}
)

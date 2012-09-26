project(Torque3D)
cmake_minimum_required(VERSION 2.8)

include(CMakeDependentOption)

CMAKE_DEPENDENT_OPTION(TORQUE_FULL_BUILD "Set the Torque3D to the Full build" OFF
	"NOT TORQUE_FULL_PHYSX_BUILD; NOT TORQUE_EMPTY_BUILD; NOT TORQUE_EMPTY_PHYSX_BUILD" OFF)

CMAKE_DEPENDENT_OPTION(TORQUE_FULL_PHYSX_BUILD "Set the Torque3D to the Full PhysX build" OFF
	"NOT TORQUE_FULL_BUILD; NOT TORQUE_EMPTY_BUILD; NOT TORQUE_EMPTY_PHYSX_BUILD" OFF)

CMAKE_DEPENDENT_OPTION(TORQUE_EMPTY_BUILD "Set the Torque3D to the Empty build" OFF
	"NOT TORQUE_FULL_BUILD; NOT TORQUE_FULL_PHYSX_BUILD; NOT TORQUE_EMPTY_PHYSX_BUILD" OFF)

CMAKE_DEPENDENT_OPTION(TORQUE_EMPTY_PHYSX_BUILD "Set the Torque3D to the Empty PhysX build" OFF
	"NOT TORQUE_FULL_BUILD; NOT TORQUE_FULL_PHYSX_BUILD; NOT TORQUE_EMPTY_BUILD" OFF)

option(TORQUE_DEDICATED "Build Torque dedicated server" OFF)

if(${TORQUE_DEDICATED})
	add_definitions(-DTORQUE_DEDICATED)
endif(${TORQUE_DEDICATED})

if(${TORQUE_FULL_BUILD})
	set(TORQUE_BUILD "Full")
elseif(${TORQUE_FULL_PHYSX_BUILD})
	set(TORQUE_BUILD "Full_PhysX")
elseif(${TORQUE_EMPTY_BUILD})
	set(TORQUE_BUILD "Empty")
elseif(${TORQUE_EMPTY_PHYSX_BUILD})
	set(TORQUE_BUILD "Empty_PhysX")
else()
	message(FATAL_ERROR "No build selected")
endif(${TORQUE_FULL_BUILD})

include_directories(
	${CMAKE_SOURCE_DIR}
	${CMAKE_CURRENT_BINARY_DIR}
)

set(TORQUE_ENGINE_PRODUCT 0006)
set(TORQUE_APP_NAME ${TORQUE_BUILD})
set(TORQUE_APP_VERSION 2009)
set(TORQUE_APP_VERSION_STRING  "2009")
set(TORQUE_MULTITHREAD TRUE)
set(TORQUE_DISABLE_MEMORY_MANAGER FALSE)
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
	-DTORQUE_OGGVORIBS
	-DTORQUE_COLLADA
	-DDOM_INCLUDE_TINYXML
	-DPCRE_STATIC
)

configure_file(cmake/torqueConfig.h.in torqueConfig.h)

add_subdirectory(main)
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

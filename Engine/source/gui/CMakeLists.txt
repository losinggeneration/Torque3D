add_subdirectory(3d)
add_subdirectory(buttons)
add_subdirectory(containers)
add_subdirectory(controls)
add_subdirectory(core)
add_subdirectory(editor)
add_subdirectory(game)
add_subdirectory(shiny)
add_subdirectory(utility)
add_subdirectory(worldEditor)

if(NOT TORQUE_DEDICATED)
	add_subdirectory(theora)
endif()

# Hack... Otherwise the add_src & add_headers macros don't properly get
# propagated up to the parent scope
file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/lib.cpp "//\n")
add_srcs(lib.cpp)

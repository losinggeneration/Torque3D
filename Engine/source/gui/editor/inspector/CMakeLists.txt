set(TORQUE_GUI_EDITOR_INSPECTOR_SRCS
	customField.cpp
	datablockField.cpp
	dynamicField.cpp
	dynamicGroup.cpp
	field.cpp
	group.cpp
	variableField.cpp
	variableGroup.cpp
	variableInspector.cpp
)

set(TORQUE_GUI_EDITOR_INSPECTOR_HEADERS
	customField.h
	datablockField.h
	dynamicField.h
	dynamicGroup.h
	field.h
	group.h
	variableField.h
	variableGroup.h
	variableInspector.h
)

add_subdirectory(inspector)

add_library(${TORQUE_BUILD}_gui_editor_inspector STATIC ${TORQUE_GUI_EDITOR_INSPECTOR_SRCS} ${TORQUE_GUI_EDITOR_INSPECTOR_HEADERS})
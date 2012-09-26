set(TORQUE_UTIL_SRCS
	catmullRom.cpp
	fpsTracker.cpp
	imposterCapture.cpp
	messaging/dispatcher.cpp
	messaging/eventManager.cpp
	messaging/message.cpp
	messaging/messageForwarder.cpp
	messaging/scriptMsgListener.cpp
	noise2d.cpp
	quadTreeTracer.cpp
	rectClipper.cpp
	sampler.cpp
	settings.cpp
	triBoxCheck.cpp
	triRayCheck.cpp
	undo.cpp
)

set(TORQUE_UTIL_HEADERS
	catmullRom.h
	fpsTracker.h
	imposterCapture.h
	interpolatedChangeProperty.h
	messaging/dispatcher.h
	messaging/eventManager.h
	messaging/message.h
	messaging/messageForwarder.h
	messaging/scriptMsgListener.h
	noise2d.h
	quadTreeTracer.h
	rectClipper.h
	returnType.h
	sampler.h
	scopeTracker.h
	settings.h
	tempAlloc.h
	triBoxCheck.h
	triRayCheck.h
	undo.h
)

add_library(${TORQUE_BUILD}_util STATIC ${TORQUE_UTIL_SRCS} ${TORQUE_UTIL_HEADERS})


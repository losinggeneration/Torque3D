add_srcs(
	main.cpp
)

add_definitions(-DTORQUE_SHARED)
add_executable(${TORQUE_BUILD} ${TORQUE_main_SRCS})
target_link_libraries(${TORQUE_BUILD} dl)


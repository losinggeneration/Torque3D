set(TORQUE_UNIT_SRCS
	consoleTest.cpp
	memoryTester.cpp
	test.cpp
	tests/testComponents.cpp
	tests/testDefaultConstruction.cpp
	tests/testMatrixMul.cpp
	tests/testRuntimeClassRep.cpp
	tests/testSwizzle.cpp
	tests/testThreadStatic.cpp
	tests/testThreadStaticPerformance.cpp
	tests/testVector.cpp
	unitTestComponentInterface.cpp
)

set(TORQUE_UNIT_HEADERS
	memoryTester.h
	test.h
	unitTestComponentInterface.h
)

add_library(${TORQUE_BUILD}_unit STATIC ${TORQUE_UNIT_SRCS} ${TORQUE_UNIT_HEADERS})


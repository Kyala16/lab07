cmake_minimum_required(VERSION 3.4)

project(solve)

add_executable(solve equation.cpp)

set_target_properties(
	solve PROPERTIES
	CXX_STANDARD 11
	CXX_STANDARD_REQUIRED ON
)

target_include_directories(
	solve
	PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib
)

target_include_directories(
	solve
	PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib
)

target_link_libraries(solve formatter_ex)
target_link_libraries(solve solver)

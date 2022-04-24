cmake_minimum_required(VERSION 3.4)

project(
	"Hello-world"
	VERSION 1.0.0
)

add_subdirectory(formatter_lib)
add_subdirectory(formatter_ex_lib)
add_subdirectory(solver_lib)
add_subdirectory(solver_application)

add_executable(${PROJECT_NAME})

target_sources(
	${PROJECT_NAME}
	PRIVATE
	main.cpp
)

target_link_libraries(${PROJECT_NAME} PRIVATE solver)


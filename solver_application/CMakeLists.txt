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

option(Generator "generator" DEFAULT)


if(${Generator} MATCHES ARC)
	install(FILES equation.cpp DESTINATION src)
	install(TARGETS formatter_ex solver LIBRARY DESTINATION lib)
endif()
if(${Generator} MATCHES RPM)
	set(CPACK_GENERATOR "RPM")
	install(TARGETS solve DESTINATION bin)
endif()
if(${Generator} MATCHES DEB)
	set(CPACK_GENERATOR "DEB")
	install(TARGETS solve DESTINATION bin)
endif()
if(${Generator} MATCHES MSI)
	set(CPACK_GENERATOR "WIX")
	install(TARGETS solve DESTINATION bin)
endif()
if(${Generator} MATCHES DMG)
	set(MACOSX_BUNDLE TRUE)
	set(CPACK_GENERATOR "DragNDrop")
	install(TARGETS solve DESTINATION bin)
endif()

include(InstallRequiredSystemLibraries)
set(CPACK_PACKEGE_NAME "Solve")
set(CPACK_PACKAGE_VENDOR "Solve equation")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "artem.myakishev.2018@mail.ru")
set(CPACK_PACKAGE_VERSION_MAJOR 1)
set(CPACK_PACKAGE_VERSION_MINOR 0)
include(CPack)

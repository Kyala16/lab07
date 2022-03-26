cmake_minimum_required(VERSION 3.4)

project(main2)

add_library(
	solver STATIC
		solver.cpp
		solver.h
)

set_target_properties(
	solver PROPERTIES
	CXX_STANDARD 11
	CXX_STANDARD_REQUIRED ON
)


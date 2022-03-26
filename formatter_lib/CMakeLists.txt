cmake_minimum_required(VERSION 3.4)

project(cmake)

add_library(
	formatter STATIC 
		formatter.cpp
		formatter.h
)

set_target_properties(
	formatter PROPERTIES
	CXX_STANDART 11
	CXX_STANDARD_REQUIRED ON
)



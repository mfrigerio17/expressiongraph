cmake_minimum_required(VERSION 2.4.6)

set(PROJECT_NAME "ExpressionTree")

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

OPTION(ENABLE_EXAMPLES "enable compilation of a series of examples" ON) 
INCLUDE(${PROJECT_SOURCE_DIR}/examples/CMakeLists.txt)

FILE( GLOB EXPRESSIONTREE_SRCS src/[^.]*.cpp src/[^.]*.cxx)

include_directories(./include)
add_library(${PROJECT_NAME} ${EXPRESSIONTREE_SRCS})

# This one requires gtest... so comment it out
#add_executable( expressiongraph_test ./tests/expressiongraph_test.cpp )
#target_link_libraries(expressiongraph_test ${PROJECT_NAME} orocos-kdl)


 

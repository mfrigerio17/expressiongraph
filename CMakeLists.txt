cmake_minimum_required(VERSION 3.0.0)

set(PROJECT_NAME "expressiongraph")

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

OPTION(ENABLE_EXAMPLES "enable compilation of a series of examples" ON) 
INCLUDE(${PROJECT_SOURCE_DIR}/examples/CMakeLists.txt)

FILE( GLOB EXPRESSIONTREE_SRCS src/[^.]*.cpp src/[^.]*.cxx)

include_directories(./include)
add_library(${PROJECT_NAME} SHARED ${EXPRESSIONTREE_SRCS})
target_link_libraries(${PROJECT_NAME} orocos-kdl)

# This one requires gtest... so comment it out
#add_executable( expressiongraph_test ./tests/expressiongraph_test.cpp )
#target_link_libraries(expressiongraph_test ${PROJECT_NAME} orocos-kdl)


set(ETASL_INSTALL_ROOT ${PROJECT_SOURCE_DIR}/../install CACHE PATH "Where to install stuff")

install(DIRECTORY include/
        DESTINATION ${ETASL_INSTALL_ROOT}/include
        FILES_MATCHING PATTERN "*.hpp")

install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION ${ETASL_INSTALL_ROOT}/lib)

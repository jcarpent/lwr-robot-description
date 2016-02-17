#
# The find_package macro for Orocos-RTT works best with
# cmake >= 2.6.3
#
cmake_minimum_required(VERSION 2.6.3)

#
# This creates a standard cmake project. You may extend this file with
# any cmake macro you see fit.
#
project(LWRRobotDescription)

file(GLOB DEPLOY_FILES_AND_DIRS "${PROJECT_SOURCE_DIR}/*")
foreach(ITEM ${DEPLOY_FILES_AND_DIRS})
   IF( IS_DIRECTORY "${ITEM}" )
      IF( NOT ( "${ITEM}" EQUAL "build" ) OR ( "${ITEM}" EQUAL ".git" ))
        LIST( APPEND DIRS_TO_DEPLOY "${ITEM}" )
      ENDIF()
   ELSE()
      IF( NOT ( "${ITEM}" EQUAL "CMakeLists.txt" ) OR ( "${ITEM}" EQUAL "README.md" ))
        LIST( APPEND FILES_TO_DEPLOY "${ITEM}" )
      ENDIF()
   ENDIF()
endforeach()
INSTALL( FILES ${FILES_TO_DEPLOY} DESTINATION etc/lwr-robot-description)
INSTALL( DIRECTORY ${DIRS_TO_DEPLOY} DESTINATION etc/lwr-robot-description)
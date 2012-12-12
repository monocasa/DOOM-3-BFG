CMAKE_MINIMUM_REQUIRED( VERSION 2.6 )

PROJECT( Doom3 )

SET( EXE_NAME doom3 )

SET( IDLIB_ROOT idlib )
SET( IDLIB_FILES ${IDLIB_ROOT}/bv/Bounds.cpp 
#                 ${IDLIB_ROOT}/bv/Box.cpp 
#                 ${IDLIB_ROOT}/bv/Sphere.cpp 
)

SET( SYS_ROOT sys/wii-ogc )
SET( SYS_FILES ${SYS_ROOT}/main.cpp )

SET( CORE_FILES #${JPEG_FILES}
#                ${OGG_FILES}
#                ${RENDERER_FILES}
#                ${FRAMEWORK_FILES}
#                ${CM_FILES}         # Doesn't link
#                ${DMAP_FILES}       # Doesn't link
#                ${AAS_FILES}        # Doesn't link
#                ${ROQ_FILES}
#                ${RENDERBUMP_FILES}
#                ${SND_FILES}        # Doesn't build, needs OpenAL
#                ${UI_FILES}
                ${SYS_FILES} )

ADD_EXECUTABLE( ${EXE_NAME} 
#                    ${IDLIB_FILES}
#                    ${GAME_FILES}
                     ${CORE_FILES} )

TARGET_LINK_LIBRARIES( ${EXE_NAME} ${TARGET_SYSTEM_LIBRARIES} )

ADD_DEFINITIONS( -g -Wall -DGEKKO -mrvl -mcpu=750 -meabi -mhard-float )

SET_TARGET_PROPERTIES( ${EXE_NAME}
	PROPERTIES
	LINK_FLAGS "-g -DGEKKO -mrvl -mcpu=750 -meabi -mhard-float"
	COMPILER_FLAGS "-g -Wall -DGEKKO -mrvl -mspu=750 -meabi -mhard-float" )

EXEFIXUP( ${EXE_NAME} )


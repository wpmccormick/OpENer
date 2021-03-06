#######################################
# CIP library                         #
#######################################

#######################################
# Add common includes                 #
#######################################
opener_common_includes()

#######################################
# Add platform-specific includes      #
#######################################
opener_platform_support("INCLUDES")

set( CIP_SRC appcontype.c cipassembly.c cipclass3connection.c cipcommon.c cipconnectionobject.c cipconnectionmanager.c ciperror.h cipethernetlink.c cipidentity.c cipioconnection.c cipmessagerouter.c ciptcpipinterface.c ciptypes.h cipepath.h cipepath.c cipelectronickey.h cipelectronickey.c cipqos.c )

add_library( CIP ${CIP_SRC} )

if( BUILD_SHARED_LIBS )
  target_link_libraries(CIP ENET_ENCAP)
  install(TARGETS CIP
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR}
  )
  install(DIRECTORY ${CIP_SRC_DIR}
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
    FILES_MATCHING PATTERN "*.h"
   )
endif( BUILD_SHARED_LIBS )

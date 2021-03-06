include_directories(${ELASTICLIENT_INCLUDE_DIRS}
                    ${CPR_INCLUDE_DIRS}
                    ${JSONCPP_INCLUDE_DIRS})

add_library(${ELASTICLIENT_LIBRARY} SHARED
            client.cc
            bulk.cc
            scroll.cc
            logging.cc

            "${ELASTICLIENT_INCLUDE_DIR}/elasticlient/client.h"
            "${ELASTICLIENT_INCLUDE_DIR}/elasticlient/logging.h"
            "${ELASTICLIENT_INCLUDE_DIR}/elasticlient/bulk.h"
            "${ELASTICLIENT_INCLUDE_DIR}/elasticlient/scroll.h")

target_link_libraries(${ELASTICLIENT_LIBRARY}
                      ${JSONCPP_LIBRARIES}
                      ${CPR_LIBRARIES})

set_target_properties(${ELASTICLIENT_LIBRARY}
                      PROPERTIES
                          VERSION "${ELASTICLIENT_VERSION_MAJOR}.${ELASTICLIENT_VERSION_MINOR}.${ELASTICLIENT_VERSION_PATCH}"
                          SOVERSION ${ELASTICLIENT_VERSION_MAJOR})

install(TARGETS ${ELASTICLIENT_LIBRARY} LIBRARY
        DESTINATION lib)

set(LIB_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/nedclib2.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/nes.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbin/binraw.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbin/rs.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbmp/address.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbmp/dcs_decode.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbmp/dcs_encode.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbmp/rawbmp.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/vpk/vpk.cpp
)

set(LIB_HEADERS
    ${CMAKE_CURRENT_SOURCE_DIR}/nedclib2.h
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbin/rs.h
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbmp/dcs.h
)

add_library(nedclib SHARED ${LIB_SOURCES} ${LIB_HEADERS})

# put all outputs in the top-level binary dir
set_target_properties(nedclib PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}"
  LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}"
  ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}"
)

# when building the shared library, define the export macro used in your headers
target_compile_definitions(nedclib PRIVATE NEDCLIB2_EXPORTS)

target_include_directories(nedclib PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbin
    ${CMAKE_CURRENT_SOURCE_DIR}/rawbmp
    ${CMAKE_CURRENT_SOURCE_DIR}/vpk
)

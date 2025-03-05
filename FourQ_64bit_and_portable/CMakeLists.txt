
set(TARGETNAME FourQ)
rbx_add_library(${TARGETNAME})
include(Sources.cmake)

set_target_properties (${TARGETNAME} PROPERTIES FOLDER Libs)

target_compile_definitions(${TARGETNAME} PRIVATE
  "__WINDOWS__"
)
target_include_directories(${TARGETNAME} PUBLIC
 "."
)
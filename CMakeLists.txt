add_definitions( -DWREN_SANDBOX=1 )

add_library( wren
                src/vm/wren_core.c
                src/vm/wren_compiler.c
                src/vm/wren_utils.c
                src/vm/wren_primitive.c
                src/vm/wren_vm.c
                src/vm/wren_value.c
                src/vm/wren_debug.c
                src/vm/Wren++.cpp 
              )

target_include_directories( wren PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/src/include" ${Boost_INCLUDE_DIR})
set_property(TARGET wren PROPERTY CXX_STANDARD 14)

install( TARGETS
   wren

   RUNTIME DESTINATION bin
   LIBRARY DESTINATION lib
   ARCHIVE DESTINATION lib
)
install( FILES ${HEADERS} DESTINATION "include/wren" )

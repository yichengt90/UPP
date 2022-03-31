#
#set( upp_test_scripts
#  compile_upp.sh
#  detect_machine.sh
#)

#
#foreach(FILENAME ${upp_test_scripts})
#    execute_process( COMMAND ${CMAKE_COMMAND} -E create_symlink
#           ${CMAKE_CURRENT_SOURCE_DIR}/${FILENAME}
#           ${CMAKE_CURRENT_BINARY_DIR}/${FILENAME} )
#endforeach(FILENAME)

# TODO add a more meaningful test? or not ...
add_test ( NAME test_build
           COMMAND bash compile_upp.sh -w
           WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/tests )

add_test ( NAME test_fv3lam
           COMMAND bash run_upp.sh
           WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/tests )

set_property(TEST test_fv3lam APPEND PROPERTY DEPENDS test_build)

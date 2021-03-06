
add_executable(AppTest ./AppTest.cpp ${SOURCES_CPP} ${SOURCES_CU} )
add_executable(CudaMeshTest ./CudaMeshTest.cpp ${SOURCES_CPP} ${SOURCES_CU} )
add_executable(CudaUtilsTest ./CudaUtilsTest.cpp ${SOURCES_CPP} ${SOURCES_CU} )
add_executable(FileReaderTest ./FileReaderTest.cpp ${SOURCES_CPP} ${SOURCES_CU} )
add_executable(GeometryHandlerTest ./GeometryHandlerTest.cpp ${SOURCES_CPP} ${SOURCES_CU} )
add_executable(MaterialHandlerTest ./MaterialHandlerTest.cpp ${SOURCES_CPP} ${SOURCES_CU} )
add_executable(VoxelizerTest ./VoxelizerTest.cpp ${SOURCES_CPP} ${SOURCES_CU} )

message(STATUS "Unit test framework: ${Boost_UNIT_TEST_FRAMEWORK_LIBRARY} ")
message(STATUS "Boost system: ${Boost_SYSTEM_LIBRARY} ")

target_link_libraries( AppTest  ${GLUT_LIBRARIES} ${OPENGL_LIBRARIES} ${GLEW_LIBRARIES}
                                ${VOXELIZER_LIB}
                                ${Boost_THREAD_LIBRARY} ${Boost_SYSTEM_LIBRARY}
                                ${Boost_CHRONO_LIBRARY}
                                ${Boost_DATE_TIME_LIBRARY} ${unix_specific_libraries}
                                ${Boost_UNIT_TEST_FRAMEWORK_LIBRARY})

target_link_libraries( CudaMeshTest ${GLUT_LIBRARIES} ${OPENGL_LIBRARIES} ${GLEW_LIBRARIES}
                                    ${VOXELIZER_LIB}
                                    ${Boost_THREAD_LIBRARY} ${Boost_SYSTEM_LIBRARY}
                                    ${Boost_CHRONO_LIBRARY}
                                    ${Boost_DATE_TIME_LIBRARY} ${unix_specific_libraries}
                                    ${Boost_UNIT_TEST_FRAMEWORK_LIBRARY})

target_link_libraries( CudaUtilsTest ${GLUT_LIBRARIES} ${OPENGL_LIBRARIES} ${GLEW_LIBRARIES}
                                    ${VOXELIZER_LIB}
                                    ${Boost_THREAD_LIBRARY} ${Boost_SYSTEM_LIBRARY}
                                    ${Boost_CHRONO_LIBRARY}
                                    ${Boost_DATE_TIME_LIBRARY} ${unix_specific_libraries}
                                    ${Boost_UNIT_TEST_FRAMEWORK_LIBRARY})

target_link_libraries( FileReaderTest ${GLUT_LIBRARIES} ${OPENGL_LIBRARIES} ${GLEW_LIBRARIES}
                                      ${VOXELIZER_LIB}
                                      ${Boost_THREAD_LIBRARY} ${Boost_SYSTEM_LIBRARY}
                                      ${Boost_CHRONO_LIBRARY}
                                      ${Boost_DATE_TIME_LIBRARY} ${unix_specific_libraries}
                                      ${Boost_UNIT_TEST_FRAMEWORK_LIBRARY})

target_link_libraries( GeometryHandlerTest ${GLUT_LIBRARIES} ${OPENGL_LIBRARIES} ${GLEW_LIBRARIES}
                                    ${VOXELIZER_LIB}
                                    ${Boost_THREAD_LIBRARY} ${Boost_SYSTEM_LIBRARY}
                                    ${Boost_CHRONO_LIBRARY}
                                    ${Boost_DATE_TIME_LIBRARY} ${unix_specific_libraries}
                                    ${Boost_UNIT_TEST_FRAMEWORK_LIBRARY})

target_link_libraries( MaterialHandlerTest ${GLUT_LIBRARIES} ${OPENGL_LIBRARIES} ${GLEW_LIBRARIES}
                                    ${VOXELIZER_LIB}
                                    ${Boost_THREAD_LIBRARY} ${Boost_SYSTEM_LIBRARY}
                                    ${Boost_CHRONO_LIBRARY}
                                    ${Boost_DATE_TIME_LIBRARY} ${unix_specific_libraries}
                                    ${Boost_UNIT_TEST_FRAMEWORK_LIBRARY})

target_link_libraries( VoxelizerTest ${GLUT_LIBRARIES} ${OPENGL_LIBRARIES} ${GLEW_LIBRARIES}
                                    ${VOXELIZER_LIB}
                                    ${Boost_THREAD_LIBRARY} ${Boost_SYSTEM_LIBRARY}
                                    ${Boost_CHRONO_LIBRARY}
                                    ${Boost_DATE_TIME_LIBRARY} ${unix_specific_libraries}
                                    ${Boost_UNIT_TEST_FRAMEWORK_LIBRARY})

if(BUILD_VOXELIZER)
   add_dependencies(MaterialHandlerTest Voxelizer)
   add_dependencies(VoxelizerTest Voxelizer)
   add_dependencies(AppTest Voxelizer)
   add_dependencies(CudaMeshTest Voxelizer)
   add_dependencies(CudaUtilsTest Voxelizer)
   add_dependencies(FileReaderTest Voxelizer)
   add_dependencies(GeometryHandlerTest Voxelizer)
endif()


set_target_properties( CudaMeshTest PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/ )
set_target_properties( CudaUtilsTest PROPERTIES ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/ )
set_target_properties( FileReaderTest PROPERTIES ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/ )
set_target_properties( GeometryHandlerTest PROPERTIES ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/ )

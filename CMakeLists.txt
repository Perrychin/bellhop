cmake_minimum_required(VERSION 3.26)
project(bellhopexe)
enable_language(Fortran)
set(CMAKE_Fortran_MODULE_DIRECTORY ${CMAKE_BINARY_DIR}/fortran_prj/module)


set(srcs_2D 

    bellhop.f90
    angleMod.f90
    ArrMod.f90
    bdryMod.f90
    bellhopMod.f90
    Cone.f90
    influence.f90
    RayNormals.f90
    ReadEnvironmentBell.f90
    ReflectMod.f90
    sspMod.f90
    Step.f90
    WriteRay.f90
)

set(srcs_3D 
bellhop3D.f90
angleMod.f90
ArrMod.f90
bdry3DMod.f90
bdryMod.f90
bellhopMod.f90
Cone.f90
influence.f90
influence3D.f90
RayNormals.f90
ReadEnvironmentBell.f90
ReflectMod.f90
Reflect3DMod.f90
sspMod.f90
Step.f90
Step3DMod.f90

WriteRay.f90
)




# add_library(${PROJECT_NAME}
#     STATIC
#         ${srcs}
# )
add_executable(bellhop2D ${srcs_2D})
add_executable(bellhop3D ${srcs_3D})


set_target_properties(bellhop2D PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out
    ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out
)

add_dependencies(bellhop2D bellhopMisc)
target_link_libraries(bellhop2D bellhopMisc)



set_target_properties(bellhop3D PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out
    ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out
)

add_dependencies(bellhop3D bellhopMisc)
target_link_libraries(bellhop3D bellhopMisc)
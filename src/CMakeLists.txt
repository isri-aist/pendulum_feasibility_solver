add_library(${PROJECT_NAME} SHARED)
target_sources(
    ${PROJECT_NAME}
    PRIVATE
        feasibility_solver.cpp
        timing_solver.cpp
        steps_solver.cpp
        polygons.cpp
)

jrl_target_headers(
  ${PROJECT_NAME}
  PUBLIC HEADERS
  ../include/pendulum_feasibility_solver/feasibility_solver.h
  ../include/pendulum_feasibility_solver/polygons.h
  BASE_DIRS
  ../include
)

target_link_libraries(
    ${PROJECT_NAME}
    PUBLIC
        SpaceVecAlg::SpaceVecAlg
        eigen-quadprog::eigen-quadprog
        Boost::headers # for boost geometry
)
target_include_directories(
    ${PROJECT_NAME}
    PUBLIC
        "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>"
        "$<INSTALL_INTERFACE:include>"
)

jrl_add_export_component(NAME ${PROJECT_NAME} TARGETS ${PROJECT_NAME})

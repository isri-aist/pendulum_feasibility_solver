cmake_minimum_required(VERSION 3.22)

include(cmake/get-jrl-cmakemodules.cmake)

project(pendulum_feasibility_solver LANGUAGES CXX VERSION 0.1.0)

jrl_configure_defaults()

# find_package(ScsEigen REQUIRED)
jrl_find_package(Boost REQUIRED EXPECTED_TARGETS Boost::headers)
jrl_find_package(SpaceVecAlg REQUIRED EXPECTED_TARGETS SpaceVecAlg::SpaceVecAlg)
jrl_find_package(eigen-quadprog REQUIRED EXPECTED_TARGETS eigen-quadprog::eigen-quadprog)

add_subdirectory(src)

# Export the package files (headers, targets, config files, etc.)
jrl_export_package()
# Print summaries
jrl_print_dependencies_summary()
jrl_print_options_summary()

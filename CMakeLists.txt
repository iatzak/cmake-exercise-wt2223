cmake_minimum_required(VERSION "3.12")

project("CMakeExercise")

find_package(Boost REQUIRED COMPONENTS filesystem)

find_package(yaml-cpp REQUIRED CONFIG)

FIND_PACKAGE(deal.II REQUIRED	
  HINTS ${DEAL_II_DIR} ../ ../../ $ENV{DEAL_II_DIR}
  )
DEAL_II_INITIALIZE_CACHED_VARIABLES()

add_executable(main main.cpp flatset/flatset.cpp filesystem/filesystem.cpp fem/fem.cpp yamlParser/yamlParser.cpp)

DEAL_II_SETUP_TARGET(main)

target_link_libraries(main Boost::filesystem yaml-cpp)

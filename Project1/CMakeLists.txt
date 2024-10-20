cmake_minimum_required(VERSION 3.1)
project(Triangulation)

set(CMAKE_CXX_STANDARD 11)


# Εύρεση της βιβλιοθήκης CGAL
find_package(CGAL REQUIRED)

# Εύρεση της βιβλιοθήκης Boost
find_package(Boost REQUIRED)
include_directories(${Boost_INCLUDE_DIRS})

# Εύρεση των απαιτούμενων βιβλιοθηκών
include_directories(${CGAL_INCLUDE_DIRS})
link_directories(${CGAL_LIBRARY_DIRS})

# Προσθήκη των πηγών
add_executable(triangulation src/main.cpp src/triangulation.cpp)

# Προσθήκη του include φακέλου για το json.hpp
target_include_directories(triangulation PRIVATE include)

# Σύνδεση της CGAL και Boost βιβλιοθήκης
target_link_libraries(triangulation CGAL::CGAL ${Boost_LIBRARIES})
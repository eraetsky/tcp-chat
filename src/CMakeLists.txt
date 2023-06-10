cmake_minimum_required(VERSION 3.12)
project(HelloCmake)

# Set C++ standard to C++11
set(CMAKE_CXX_STANDARD 11)

# Find Boost
find_package(Boost REQUIRED COMPONENTS system)

# Specify include directories
include_directories(${PROJECT_SOURCE_DIR}/include ${Boost_INCLUDE_DIRS})

# Specify source files for client
set(CLIENT_SOURCES 
    ${PROJECT_SOURCE_DIR}/cpps/client.cpp
)

# Create an executable for client
add_executable(Client ${CLIENT_SOURCES})

# Link against Boost libraries for client
target_link_libraries(Client ${Boost_LIBRARIES})

# Specify source files for server
set(SERVER_SOURCES 
    ${PROJECT_SOURCE_DIR}/cpps/server.cpp
)

# Create an executable for server
add_executable(Server ${SERVER_SOURCES})

# Link against Boost libraries for server
target_link_libraries(Server ${Boost_LIBRARIES})

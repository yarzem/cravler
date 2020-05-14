cmake_minimum_required(VERSION 3.15)
include("tools/gate/cmake/HunterGate.cmake")

HunterGate(
        URL "https://github.com/cpp-pm/hunter/archive/v0.23.218.tar.gz"
        SHA1 "9a3594a61227967fb92159339ba326701b287b19"
)
project(cravler)
hunter_add_package(Boost COMPONENTS log thread)
find_package(Boost CONFIG REQUIRED log thread)
hunter_add_package(OpenSSL)
find_package(OpenSSL REQUIRED)
hunter_add_package(gumbo)
find_package(gumbo CONFIG REQUIRED)

set(CMAKE_CXX_STANDARD 17)

add_executable(cravler main.cpp)
target_link_libraries(cravler Boost::log gumbo::gumbo Boost::thread OpenSSL::SSL)
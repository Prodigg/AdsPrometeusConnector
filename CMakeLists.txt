cmake_minimum_required(VERSION 4.1)
project(CppAdsPrometheusConnector)

set(CMAKE_CXX_STANDARD 23)
#add_subdirectory(external/ADS/include/AdsLib)
include_directories(external/ADS/include/AdsLib)
include_directories(external/libpistacheStatic/include)

add_executable(CppAdsPrometheusConnector
        src/main.cpp
        src/ProcessDataBuffer.h
        src/ProcessDataBuffer.cpp
        src/ADSProvidor.h
        src/ADSProvidor.cpp
        src/PrometheusEndpoint.h
        src/PrometheusEndpoint.cpp
        src/Configuration.h
        src/Configuration.cpp
)

include(FetchContent)

FetchContent_Declare(json URL https://github.com/nlohmann/json/releases/download/v3.12.0/json.tar.xz)
FetchContent_MakeAvailable(json)

target_link_libraries(CppAdsPrometheusConnector PRIVATE nlohmann_json::nlohmann_json)
target_link_libraries(CppAdsPrometheusConnector PRIVATE ${CMAKE_SOURCE_DIR}/external/ADS/lib/libAdsLib.a)
target_link_libraries(CppAdsPrometheusConnector PRIVATE ${CMAKE_SOURCE_DIR}/external/libpistacheStatic/libpistache.a)

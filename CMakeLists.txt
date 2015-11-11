project(pvr.iptvsimple)

cmake_minimum_required(VERSION 2.6)

enable_language(CXX)

find_package(mrmc REQUIRED)
find_package(mrmcplatform REQUIRED)
find_package(platform REQUIRED)
find_package(ZLIB REQUIRED)

include_directories(${mrmcplatform_INCLUDE_DIRS}
                    ${platform_INCLUDE_DIRS}
                    ${MRMC_INCLUDE_DIR}
                    ${ZLIB_INCLUDE_DIRS}
                    ${PROJECT_SOURCE_DIR}/lib)

set(DEPLIBS ${platform_LIBRARIES}
            ${ZLIB_LIBRARIES})

message(STATUS "ZLIB_LIBRARIES: ${ZLIB_LIBRARIES}")

set(IPTV_SOURCES src/client.cpp
                 src/PVRIptvData.cpp)

build_addon(pvr.iptvsimple IPTV DEPLIBS)

include(CPack)

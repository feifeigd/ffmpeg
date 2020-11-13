cmake_minimum_required(VERSION 3.2)

include(cmake/HunterGate.cmake)
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.23.214.tar.gz"
    SHA1 "e14bc153a7f16d6a5eeec845fb0283c8fad8c358"
)

project(ffmpeg)

set (CMAKE_CXX_STANDARD 17)

hunter_add_package(ffmpeg)
find_package(ffmpeg CONFIG REQUIRED)

add_executable(main main.cpp)
target_link_libraries(
    main
    PUBLIC
    ffmpeg::avcodec
    ffmpeg::avdevice
    ffmpeg::avfilter	
    ffmpeg::avformat
    ffmpeg::avutil
    ffmpeg::swresample
    ffmpeg::swscale
)

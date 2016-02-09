cmake_minimum_required(VERSION 2.6)
project(Head_unit C)

set(SRC_DIR ${PROJECT_SOURCE_DIR})

set(APP_NAME hu)

# DEBUG|RELEASE|RELWITHDEBINFO|MINSIZEREL
set(CMAKE_BUILD_TYPE DEBUG)

include_directories(${PROJECT_SOURCE_DIR})
include_directories(/usr/include/libusb-1.0)

link_directories(/usr/local/lib)

list(APPEND SRC hu_mai.c)
list(APPEND SRC hu_usb.c)
list(APPEND SRC hu_aap.c)
list(APPEND SRC hu_ssl.c)
list(APPEND SRC hu_aad.c)
list(APPEND SRC hu_uti.c)

add_executable(${APP_NAME} ${SRC})

target_link_libraries(${APP_NAME} usb-1.0)
target_link_libraries(${APP_NAME} libssl.so)
target_link_libraries(${APP_NAME} libcrypto.so -ldl)
target_link_libraries(${APP_NAME} libpthread.so)

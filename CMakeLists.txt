cmake_minimum_required(VERSION 3.12)
# Pull in SDK (must be before project)
include(pico_sdk_import.cmake)
include(pico_extras_import_optional.cmake)


project(my_blink C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# initialize the pico sdk for custom CMake commands
pico_sdk_init()

add_executable(${PROJECT_NAME}
    my_blink.c
    )

# pull in common dependencies
target_link_libraries(${PROJECT_NAME} pico_stdlib)

if (PICO_CYW43_SUPPORTED)
    target_link_libraries(${PROJECT_NAME} pico_cyw43_arch_none)
endif()

# create map/bin/hex file etc.
pico_add_extra_outputs(${PROJECT_NAME})

cmake_minimum_required(VERSION 3.20)
project(RayTracingInOneWeekend CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(RayTracingInOneWeekend
    main.cpp
    color.h
    ray.h
    vec3.h
    hittable.h
    hittable_list.h
    rtweekend.h
    sphere.h
    interval.h
)

set(PPM_OUTPUT "${CMAKE_CURRENT_SOURCE_DIR}/image.ppm")

add_custom_command(TARGET RayTracingInOneWeekend POST_BUILD
    COMMAND RayTracingInOneWeekend > "${PPM_OUTPUT}"
    COMMAND ${CMAKE_COMMAND} -E echo "Rendered ${PPM_OUTPUT}"
    COMMAND cmd /c start "" "${PPM_OUTPUT}"
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Rendering to PPM and opening it"
)

set(FILTER htwk_ipm)

adtf_add_filter(
        ${FILTER}
        stdafx.h
        stdafx.cpp
        ipm.h
        ipm.cpp
)

adtf_install_plugin(${FILTER} ${CMAKE_INSTALL_PREFIX}/filter)

add_subdirectory(./../htwk_logger htwk_logger)
add_subdirectory(./../htwk_vision htwk_vision)

include_directories(${OpenCV_INCLUDE_DIR})
include_directories(${HTWK_LOGGER_INCLUDE_DIR})
include_directories(${HTWK_VISION_INCLUDE_DIR})

target_link_libraries(${FILTER} htwk_logger)
target_link_libraries(${FILTER} htwk_vision)
target_link_libraries(${FILTER} htwk_utils)
target_link_libraries(${FILTER} htwk_structs)
target_link_libraries(${FILTER} ${OpenCV_LIBS})
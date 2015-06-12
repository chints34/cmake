cmake_minimum_required (VERSION 2.8)
project (hello)

set(DIR_src src)

#get_filename_component(MAIN_SRC ${DIR_src} ABSOLUTE)
FILE(GLOB SRC_FILES
	${DIR_src}/*
) 
#LINK_LIBRARIES(pthread)

INCLUDE_DIRECTORIES(/home/chints/cmake/Include/)
LINK_DIRECTORIES(/home/chints/cmake/lib/)

#add_library(mylib SHARED ${SRC_FILES})

add_executable(main ${SRC_FILES})

TARGET_LINK_LIBRARIES(main hello)
add_custom_command(TARGET main 
PRE_BUILD 
COMMAND ${CMAKE_COMMAND} -E cp /home/chints/cmake/src/main.c
/home/chints/cmake/lib
)

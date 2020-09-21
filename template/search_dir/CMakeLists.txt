CMAKE_MINIMUM_REQUIRED(VERSION 3.16)
SET(PRJ "sherlock_game")
SET(MY_LIB "${PRJ}_library")

SET(SRC  e_holmes.c;
         g_lestrade.c;
         j_moriarty.c;
         j_watson.c;
         m_holmes.c;
         m_hooper.c;
         m_hudson.c;
         m_watson.c;
         s_holmes.c)

SET(INC  inc_e_holmes.h;
         inc_g_lestrade.h;
         inc_j_moriarty.h;
         inc_j_watson.h;
         inc_m_holmes.h;
         inc_m_hooper.h;
         inc_m_hudson.h;
         inc_m_watson.h;
         inc_s_holmes.h)

IF (${CMAKE_HOST_SYSTEM_NAME} MATCHES "^MSYS" OR WIN32 OR MSVC)
	set ( CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON FORCE)
ENDIF ()

SET(SRC_DIR "${CMAKE_SOURCE_DIR}/source")
SET(INC_DIR "${CMAKE_SOURCE_DIR}/include")

list(TRANSFORM SRC PREPEND "${SRC_DIR}/")
list(TRANSFORM INC PREPEND "${INC_DIR}/")

PROJECT(${PRJ} C)

add_library(${MY_LIB} SHARED ${SRC} ${INC})

set_target_properties(${MY_LIB}
					  PROPERTIES
					  RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/lib"
					  LIBRARY_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/lib")


CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
PROJECT(TDengine)

IF ((TD_LINUX_64) OR (TD_LINUX_32 AND TD_ARM))
  INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/src/inc)
  INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/src/os/inc)
  INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/src/client/inc)
  INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/src/util/inc)
  INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/src/query/inc)
  INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/src/common/inc)
  INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/deps/zlib-1.2.11/inc)
  INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/deps/cJson/inc)
  INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/deps/lz4/inc)
  INCLUDE_DIRECTORIES(inc)
  AUX_SOURCE_DIRECTORY(src SRC)
  ADD_LIBRARY(http ${SRC})
#  TARGET_LINK_LIBRARIES(http taos_static z)
  TARGET_LINK_LIBRARIES(http taos z)

  IF (TD_ADMIN)
    TARGET_LINK_LIBRARIES(http admin)
  ENDIF ()
ENDIF ()

SET(CMAKE_LEGACY_CYGWIN_WIN32 0)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

SET(CMAKE_CXX_STANDARD 14)
INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR}/src)
SET(CMAKE_CXX_FLAGS_RELWITHDEBINFO
    "${CMAKE_CXX_FLAGS_RELWITHDEBINFO} -pg"
)
SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY
    ${PROJECT_SOURCE_DIR}/${CMAKE_BUILD_TYPE}/bin
)
SET(CMAKE_ARCHIVE_OUTPUT_DIRECTORY
    ${PROJECT_SOURCE_DIR}/${CMAKE_BUILD_TYPE}/lib
)

IF(CMAKE_BUILD_TYPE MATCHES Release)
    SET(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static")
    LINK_DIRECTORIES(${PROJECT_SOURCE_DIR}/Release/lib)
    ADD_EXECUTABLE(ecdh ecdh.cpp)
    TARGET_LINK_LIBRARIES(ecdh eccrypto)
    ADD_EXECUTABLE(ecelgamal ecelgamal.cpp)
    TARGET_LINK_LIBRARIES(ecelgamal eccrypto)
    ADD_EXECUTABLE(ecdsa ecdsa.cpp)
    TARGET_LINK_LIBRARIES(ecdsa eccrypto)
    ADD_EXECUTABLE(key key.cpp)
    TARGET_LINK_LIBRARIES(key eccrypto)
    ADD_EXECUTABLE(encrypt encrypt.cpp)
    TARGET_LINK_LIBRARIES(encrypt eccrypto)
    ADD_EXECUTABLE(decrypt decrypt.cpp)
    TARGET_LINK_LIBRARIES(decrypt eccrypto)
    ADD_EXECUTABLE(sign sign.cpp)
    TARGET_LINK_LIBRARIES(sign eccrypto)
    ADD_EXECUTABLE(verify verify.cpp)
    TARGET_LINK_LIBRARIES(verify eccrypto)
ENDIF()

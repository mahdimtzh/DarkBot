cmake_minimum_required(VERSION 3.10)
project(DarkBot)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/../bin)

set(CMAKE_CXX_FLAGS_DEBUG "/MT /Zi /Od /DDEBUG")
set(CMAKE_CXX_FLAGS_RELEASE "/MT /O2 /DNDEBUG")

include_directories(
    ${CMAKE_SOURCE_DIR}
    ${CMAKE_SOURCE_DIR}/raknet
    ${CMAKE_SOURCE_DIR}/raknet/SAMP
    ${CMAKE_SOURCE_DIR}/sqlite3
    ${CMAKE_SOURCE_DIR}/imgui
)

set(SOURCES
    console.cpp
    main.cpp
    math_stuff.cpp
    misc_funcs.cpp
    client.cpp
    netrpc.cpp

    raknet/AsynchronousFileIO.cpp
    raknet/BitStream.cpp
    raknet/BitStream_NoTemplate.cpp
    raknet/CheckSum.cpp
    raknet/DataBlockEncryptor.cpp
    raknet/DataCompressor.cpp
    raknet/DS_ByteQueue.cpp
    raknet/DS_HuffmanEncodingTree.cpp
    raknet/DS_Table.cpp
    raknet/EncodeClassName.cpp
    raknet/GetTime.cpp
    raknet/InternalPacketPool.cpp
    raknet/LinuxStrings.cpp
    raknet/NetworkIDGenerator.cpp
    raknet/NetworkTypes.cpp
    raknet/PluginInterface.cpp
    raknet/RakClient.cpp
    raknet/RakNetStatistics.cpp
    raknet/RakNetworkFactory.cpp
    raknet/RakPeer.cpp
    raknet/rakserver.cpp
    raknet/RakSleep.cpp
    raknet/Rand.cpp
    raknet/ReliabilityLayer.cpp
    raknet/rijndael.cpp
    raknet/RPCMap.cpp
    raknet/SAMP/SAMPRPC.cpp
    raknet/SAMP/samp_auth.cpp
    raknet/SAMP/samp_netencr.cpp
    raknet/SHA1.cpp
    raknet/SimpleMutex.cpp
    raknet/SocketLayer.cpp
    raknet/StringCompressor.cpp
    raknet/StringTable.cpp
    raknet/SystemAddressList.cpp
    raknet/TableSerializer.cpp
    raknet/_findfirst.cpp
)

add_executable(DarkBot ${SOURCES})

link_directories(
    ${CMAKE_SOURCE_DIR}/sqlite3
)

target_link_libraries(DarkBot
    MSVCRT
    opengl32
    ws2_32
    comctl32
)

if(MSVC)
    set_target_properties(DarkBot PROPERTIES
        LINK_FLAGS "/SUBSYSTEM:WINDOWS /MACHINE:X86"
    )
endif()

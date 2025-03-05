cmake_minimum_required(VERSION 3.25.2)
include(FetchContent)

if (CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR)
    if ("$ENV{RBX_SECURITY_CMAKE_ROOT}" STREQUAL "")
        # Fetch security-cmake prelude
        message(STATUS "Fetching security-buildsystem from github.rbx.com ...")
        message(STATUS "(To use local security-buildsystem, please define system environment variable 'RBX_SECURITY_CMAKE_ROOT')")
        FetchContent_Declare(
            security-buildsystem
            GIT_REPOSITORY git@github.rbx.com:GameEngine/security-buildsystem.git
            GIT_TAG        6df6f6814eb23b027b51acb982ce6bcfb731c853
        )
        FetchContent_MakeAvailable(security-buildsystem)
    else()
        # Use local security-cmake prelude
        message(STATUS "Use local security-buildsystem: $ENV{RBX_SECURITY_CMAKE_ROOT}/cmake")
        include("$ENV{RBX_SECURITY_CMAKE_ROOT}/cmake/rbx-prelude.cmake")
    endif()

    # Create project
    rbx_project(FourQLib C CXX)

    # Get 3rd party repos
    ## - catch2
    #FetchContent_Declare(catch2
    #    GIT_REPOSITORY    git@github.rbx.com:GameEngine/Catch2.git
    #    GIT_TAG           v3.3.2
    #)
    #FetchContent_MakeAvailable(catch2)
    #set_target_properties(Catch2 PROPERTIES FOLDER ThirdParty)
    #set_target_properties(Catch2WithMain PROPERTIES FOLDER ThirdParty)
    ## - libsodium
    #FetchContent_Declare(libsodium
    #    GIT_REPOSITORY    git@github.rbx.com:GameEngine/libsodium.git
    #    GIT_TAG           38594e55fdad31608ce7bfb468d8074799787bd4
    #)
    #FetchContent_MakeAvailable(libsodium)
    #set_target_properties(libsodium PROPERTIES FOLDER ThirdParty)
    ## - blake3
    #FetchContent_Declare(blake3
    #    GIT_REPOSITORY    git@github.rbx.com:GameEngine/blake3.git
    #    GIT_TAG           a03640ffd500652301114ca09e26feb7a79aa487
    #)
    #FetchContent_MakeAvailable(blake3)
    #set_target_properties(blake3 PROPERTIES FOLDER ThirdParty)
    ## - blake3
    #FetchContent_Declare(fourqlib
    #    GIT_REPOSITORY    https://github.com/microsoft/FourQlib.git
    #    GIT_TAG           1031567f23278e1135b35cc04e5d74c2ac88c029
    #)
    #FetchContent_MakeAvailable(fourqlib)
    #set_target_properties(fourqlib PROPERTIES FOLDER ThirdParty)

endif()

add_subdirectory(FourQ_64bit_and_portable)

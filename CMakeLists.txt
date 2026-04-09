add_library(d3d9lib INTERFACE)

# Common libraries for all compilers
target_link_libraries(d3d9lib INTERFACE d3d9 dinput8 dxguid)

# MSVC-specific configuration
if(MSVC)
    # Use bundled MSVC-compiled .lib files
    target_link_libraries(d3d9lib INTERFACE d3dx9)
    target_link_directories(d3d9lib BEFORE INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})
    target_link_options(d3d9lib INTERFACE /NODEFAULTLIB:libci.lib)
    
    if(CMAKE_CXX_COMPILER_VERSION VERSION_GREATER "12.0.8804")
        # Modern MSVC (VS 2013+) has complete DirectX headers in Windows SDK
        target_link_libraries(d3d9lib INTERFACE legacy_stdio_definitions)
        target_link_options(d3d9lib INTERFACE /SAFESEH:NO)
    else()
        # VC6 and older MSVC need extra headers - their DirectX SDK is missing newer definitions
        target_compile_definitions(d3d9lib INTERFACE D3D_DISABLE_9EX)
        target_include_directories(d3d9lib INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/extra)
    endif()
endif()

# MinGW-specific configuration
#if(MINGW)
#    # MinGW-w64 DirectX 8 support varies by architecture:
#    # i686 (32-bit): libd3d9.a + libd3dx9d.a (debug only, no release version)
#    # x86_64 (64-bit): libd3d9thk.a only (no libd3dx8 libraries at all)
#    target_link_libraries(d3d9lib INTERFACE d3dx9d)
#endif()

target_compile_definitions(d3d9lib INTERFACE -DBUILD_WITH_D3D9)
target_include_directories(d3d9lib INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})

cmake_minimum_required(VERSION 2.8)

add_library( LLVMDDG SHARED
        DDG.cpp
)
target_compile_features(LLVMDDG PRIVATE cxx_range_for cxx_auto_type)
set(CMAKE_CXX_FLAGS "-std=c++11 -Wall -fno-rtti -D__STDC_CONSTANT_MACROS -D__STDC_LIMIT_MACROS -fPIC -I/usr/local/llvm/include")
set_target_properties(LLVMDDG PROPERTIES
    COMPILE_FLAGS "-fno-rtti"
)

# If we don't need RTTI or EH, there's no reason to export anything
# from the hello plugin.
if( NOT LLVM_REQUIRES_RTTI )
    if( NOT LLVM_REQUIRES_EH )
        set(LLVM_EXPORTED_SYMBOL_FILE ${CMAKE_CURRENT_SOURCE_DIR}/DDG.exports)
    endif()
endif()

if(WIN32 OR CYGWIN)
    set(LLVM_LINK_COMPONENTS Core Support)
endif()

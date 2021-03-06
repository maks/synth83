# Sets the minimum version of CMake required to build your native library.
# This ensures that a certain set of CMake features is available to
# your build.

cmake_minimum_required(VERSION 3.4.1)


# Specifies a library name, specifies whether the library is STATIC or
# SHARED, and provides relative paths to the source code. You can
# define multiple libraries by adding multiple add_library() commands,
# and CMake builds them for you. When you build your app, Gradle
# automatically packages shared libraries with your APK.

add_library( # Specifies the name of the library.
             synth

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
             src/android_glue.cc
             src/dx7note.cc
             src/env.cc
             src/exp2.cc
             src/fir.cc
             src/fm_core.cc
             src/fm_op_kernel.cc
             src/freqlut.cc
             src/lfo.cc
             src/log2.cc
             src/patch.cc
             src/pitchenv.cc
             src/resofilter.cc
             src/ringbuffer.cc
             src/sawtooth.cc
             src/sin.cc
             src/synth_unit.cc
        )

target_compile_options(synth PRIVATE -Wno-c++11-narrowing)

include_directories("include")

# Links your native library against one or more other native libraries.
target_link_libraries( # Specifies the target library.
        synth

        # Links the log library to the target library.
        ${log-lib} )

target_link_libraries( # Specifies the target library.
                       synth

                       # Links the log library to the target library.
                       ${openSL-ES} )

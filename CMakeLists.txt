
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/lib/)

if(APPLE AND NOT IOS)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -arch x86_64")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -arch x86_64 -F/Library/Frameworks")
endif()

set(DONT_HAVE_FRIBIDI_CONFIG_H ON)
add_definitions(-DDONT_HAVE_FRIBIDI_CONFIG_H=${DONT_HAVE_FRIBIDI_CONFIG_H})
add_compile_definitions(DONT_HAVE_FRIBIDI_CONFIG_H)

set(libfribidi_headers
    lib/fribidi-arabic.h
    lib/fribidi-begindecls.h
    lib/fribidi-bidi.h
    lib/fribidi-bidi-types.h
    lib/fribidi-bidi-types-list.h
    lib/fribidi-common.h
    lib/fribidi-deprecated.h
    lib/fribidi-enddecls.h
    lib/fribidi-flags.h
    lib/fribidi-joining.h
    lib/fribidi-joining-types.h
    lib/fribidi-joining-types-list.h
    lib/fribidi-mirroring.h
    lib/fribidi-shape.h
    lib/fribidi-types.h
    lib/fribidi-unicode.h
    lib/fribidi.h
)

# fribidi
add_library(fribidi STATIC
    ${libfribidi_headers}
    lib/fribidi-arabic.c
    lib/fribidi-bidi-types.c
    lib/fribidi-bidi.c
    lib/fribidi-brackets.c
    lib/fribidi-char-sets-cap-rtl.c
    lib/fribidi-char-sets-cp1255.c
    lib/fribidi-char-sets-cp1256.c
    lib/fribidi-char-sets-iso8859-6.c
    lib/fribidi-char-sets-iso8859-8.c
    lib/fribidi-char-sets-utf8.c
    lib/fribidi-char-sets.c
    lib/fribidi-deprecated.c
    lib/fribidi-joining-types.c
    lib/fribidi-joining.c
    lib/fribidi-mirroring.c
    lib/fribidi-run.c
    lib/fribidi-shape.c
    lib/fribidi.c
)

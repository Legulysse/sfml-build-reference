# SFML Build Reference
Reference sheet for building SFML 3.  

More specifically, those are the settings I had to use for my own premake5 script when building SFML 3 and its dependencies.  
This is intended for developpers using other build systems than CMake for their projects.  

NOTE: Those settings have only been tested on Windows with Visual Studio.  
I may update this sheet with notes concerning linux builds if I have the opportunity to test my settings on a linux setup.

# Target Versions

List of all libraries used as submodules.

| Library | Version | Repository |
|---|---|---|
| SFML | 3.0.0 | https://github.com/SFML/SFML.git |
| Freetype | 2.13.2 | https://github.com/freetype/freetype.git |
| Ogg | 1.3.5 | https://github.com/xiph/ogg.git|
| Flac | 1.4.3 | https://github.com/xiph/flac.git |
| Vorbis | 1.3.7 | https://github.com/xiph/vorbis.git |

# Build Settings

## SFML

| Define | Platform | Description |
|---|---|---|
| SFML_STATIC | - | Specify if SFML is used as a static lib instead of a dynamic lib. |
| MA_NO_MP3 | - | Disable unused miniaudio features. |
| MA_NO_FLAC | - | Disable unused miniaudio features. |
| MA_NO_ENCODING | - | Disable unused miniaudio features. |
| MA_NO_RESOURCE_MANAGER | - | Disable unused miniaudio features. |
| MA_NO_GENERATION | - | Disable unused miniaudio features. |
| MA_USE_STDINT | - | Use standard fixed-width integer types. |
| STBI_FAILURE_USERMSG | - |  |
| SFML_IS_BIG_ENDIAN=0 | - |  |
| FT2_BUILD_LIBRARY | - | Used for consistency with freetype settings (Optional ?). |
| FLAC__NO_DLL | - |  |
| OV_EXCLUDE_STATIC_CALLBACKS | - |  |

Includes :
```
SFML/include
SFML/src
SFML/extlibs/headers/glad/include
SFML/extlibs/headers/mingw
SFML/extlibs/headers/miniaudio
SFML/extlibs/headers/minimp3
SFML/extlibs/headers/stb_image
SFML/extlibs/headers/vulkan
Freetype/include
Ogg/include
Flac/include
Vorbis/include
```

Sources :
```
SFML/include/**.hpp
SFML/include/**.inl
SFML/src/**.hpp
SFML/src/**.cpp
```

Excluded Sources :
```
SFML/Main/MainAndroid.cpp
SFML/Network/Unix/**
SFML/System/Android/**
SFML/System/Unix/**
SFML/Window/Android/**
SFML/Window/DRM/**
SFML/Window/FreeBSD/**
SFML/Window/iOS/**
SFML/Window/macOS/**
SFML/Window/NetBSD/**
SFML/Window/OpenBSD/**
SFML/Window/Unix/**
```

## Freetype

| Define | Platform | Description |
|---|---|---|
| FT2_BUILD_LIBRARY | - | Specify to Freetype that it is built as a library. |

Includes :
```
Freetype/include
```

Sources :
```
Freetype/src/autofit/autofit.c
Freetype/src/base/ftbase.c
Freetype/src/base/ftbbox.c
Freetype/src/base/ftbdf.c
Freetype/src/base/ftbitmap.c
Freetype/src/base/ftcid.c
Freetype/src/base/ftfstype.c
Freetype/src/base/ftgasp.c
Freetype/src/base/ftglyph.c
Freetype/src/base/ftgxval.c
Freetype/src/base/ftinit.c
Freetype/src/base/ftmm.c
Freetype/src/base/ftotval.c
Freetype/src/base/ftpatent.c
Freetype/src/base/ftpfr.c
Freetype/src/base/ftstroke.c
Freetype/src/base/ftsynth.c
Freetype/src/base/fttype1.c
Freetype/src/base/ftwinfnt.c
Freetype/src/bdf/bdf.c
Freetype/src/bzip2/ftbzip2.c
Freetype/src/cache/ftcache.c
Freetype/src/cff/cff.c
Freetype/src/cid/type1cid.c
Freetype/src/gzip/ftgzip.c
Freetype/src/lzw/ftlzw.c
Freetype/src/pcf/pcf.c
Freetype/src/pfr/pfr.c
Freetype/src/psaux/psaux.c
Freetype/src/pshinter/pshinter.c
Freetype/src/psnames/psnames.c
Freetype/src/raster/raster.c
Freetype/src/sdf/sdf.c
Freetype/src/sfnt/sfnt.c
Freetype/src/smooth/smooth.c
Freetype/src/svg/svg.c
Freetype/src/truetype/truetype.c
Freetype/src/type1/type1.c
Freetype/src/type42/type42.c
Freetype/src/winfonts/winfnt.c

Freetype/builds/windows/ftsystem.c [Windows]
Freetype/builds/windows/ftdebug.c [Windows]
```

## Ogg

No specific Defines required.

Includes :
```
Ogg/include
```

Sources :
```
Ogg/src/**.h
Ogg/src/**.c
```

## Flac

| Define | Platform | Description |
|---|---|---|
| FLAC__NO_DLL | - |  |
| CPU_IS_BIG_ENDIAN=0 | - |  |
| FLAC__HAS_OGG=1 | - |  |
| PACKAGE_VERSION=\"\" | - |  |

Includes :
```
Flac/include
Flac/src/libFLAC/include
Ogg/include
```

Sources :
```
Flac/src/libFLAC/**.c
Flac/src/share/win_utf8_io/**.c [Windows]
```

Excluded Sources :
```
Flac/src/libFLAC/deduplication/**
```

## Vorbis

| Define | Platform | Description |
|---|---|---|
| OV_EXCLUDE_STATIC_CALLBACKS | - |  |

Includes :
```
Vorbis/include
Ogg/include
```

Sources :
```
Vorbis/lib/envelope.h
Vorbis/lib/lpc.h
Vorbis/lib/lsp.h
Vorbis/lib/codebook.h
Vorbis/lib/misc.h
Vorbis/lib/psy.h
Vorbis/lib/masking.h
Vorbis/lib/os.h
Vorbis/lib/mdct.h
Vorbis/lib/smallft.h
Vorbis/lib/highlevel.h
Vorbis/lib/registry.h
Vorbis/lib/scales.h
Vorbis/lib/window.h
Vorbis/lib/lookup.h
Vorbis/lib/lookup_data.h
Vorbis/lib/codec_internal.h
Vorbis/lib/backends.h
Vorbis/lib/bitrate.h

Vorbis/lib/mdct.c
Vorbis/lib/smallft.c
Vorbis/lib/block.c
Vorbis/lib/envelope.c
Vorbis/lib/window.c
Vorbis/lib/lsp.c
Vorbis/lib/lpc.c
Vorbis/lib/analysis.c
Vorbis/lib/synthesis.c
Vorbis/lib/psy.c
Vorbis/lib/info.c
Vorbis/lib/floor1.c
Vorbis/lib/floor0.c
Vorbis/lib/res0.c
Vorbis/lib/mapping0.c
Vorbis/lib/registry.c
Vorbis/lib/codebook.c
Vorbis/lib/sharedbook.c
Vorbis/lib/lookup.c
Vorbis/lib/bitrate.c

Vorbis/lib/vorbisfile.c
Vorbis/lib/vorbisenc.c
```

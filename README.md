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

## Freetype

| Define | Platform | Description |
|---|---|---|
| FT2_BUILD_LIBRARY | - | Specify to Freetype that it is built as a library. |

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
Flac/src/share/win_utf8_io/**.c
```

Excluded Sources :
```
Flac/src/libFLAC/deduplication/**
```

## Vorbis

| Define | Platform | Description |
|---|---|---|
| OV_EXCLUDE_STATIC_CALLBACKS | - |  |

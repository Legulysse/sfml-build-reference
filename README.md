# SFML Build Reference
Reference sheet for building SFML 3.  

More specifically, those are the settings I had to use for my own premake5 script when building SFML 3 and its dependencies.  
This is intended for developpers using other build systems than CMake for their projects.  

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
| FT2_BUILD_LIBRARY | - | Used for consistency with freetype settings (Optional ?). |
| TODO | TODO | TODO |

## Freetype

| Define | Platform | Description |
|---|---|---|
| FT2_BUILD_LIBRARY | - | Specify to Freetype that it is built as a library. |

## Ogg

| Define | Platform | Description |
|---|---|---|
| TODO | TODO | TODO |

## Flac

| Define | Platform | Description |
|---|---|---|
| TODO | TODO | TODO |

## Vorbis

| Define | Platform | Description |
|---|---|---|
| TODO | TODO | TODO |

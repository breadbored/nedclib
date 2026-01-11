# Nintendo e-Reader Tools ported to multi-platform

Included tools (see [here](#documentation) for documentation):

- raw2bmp
- nevpk
- nedcmake
- nedcenc
- A ported version of nedclib.dll to be used as a C/C++ library. This can be imported into any number of languages that support C/C++ libraries such as Python, Rust, C/C++, Node (not vanilla JS), etc

## Building

CMakeLists.txt have been provided to make building on all platforms extremely easy.

- Clone the repository with `git clone`

- Install build dependencies:
  - Windows
    - Install [MSYS2](https://www.msys2.org/)
    - Install [CMake](https://cmake.org/download/)
  - macOS
    - Install CMake
      ```
      brew install cmake
      ```
  - debian
    - Install build tools and cmake
      ```
      apt install build-essential cmake
      ```

- If using Visual Studio Code, simply install the CMake Tools extension and then build. Binaries will be in `./build`.

- Otherwise, make a directory called `build`, call `cmake ..` and finally `make` to build:
  ```
  mkdir build
  cd build
  cmake ..
  make
  ```

Tested on Windows 11, macOS 26, and Debain 12.

## Why?

Because the e-Reader was a simple device to reverse engineer. These tools allow you to write ARMv7, thumb, Z80, 6502 assembly and inject code into a number of GBA games. For example, you could inject custom events into the Pokemon games.

## Documentation

### raw2bmp

```txt
Nintendo e-Reader dotcode strip tool Version 1.4
Copyrighted by CaitSith2

Usage :
  DcsTool [options]
Options :
  -i <file>             Input File                      (Required)
  -o <file>             Output File                     (Required)
  -dpi <dpi>            DPI Setting                     (Optional, Default 300)
  -MultiStrip           Multistrip raw file mode                (Optional)
```

### nevpk

```txt
Nintendo e-Reader VPK Tool Version 1.4
Copyright CaitSith2

usage :
  nvpktool [options]
options :
  -i <file>            input file                              (Required)
  -o <file>            output file                             (Required)
  -v                   verbose                                 (Optional)
  -c                   compress                                (Required *)
  -d                   decompress                              (Required *)
  -level <value>       compression level (0=store 1=med 2=max  (Default = 2)
                       3 = Discover best lzwindow/lzsize/method)
  -log <file>          Decompression log                       (Default = none)
  (following options are only valid for compression levels 1 & 2)
  -method <value>      compression method (0 or 1)             (Default = 0)
  -lzwindow <value>    lz window size                          (Default = 4096)
  -lzsize <value>      lz max repeat size                      (Default = 256)
```

### nedcmake

```txt
Nintendo E-Reader Dotcode bin maker tool Version 1.4
Copyright CaitSith2

usage :
  nedcmaker [options]
options :
  -i <file>          input file                  (required)
  -o <file>          output name                 (optional)
  -type <value>      type (0=nes 1=z80           (required)
                     2 = gba 3 = raw
  -region <value>    region (0=jap 1=usa 2=jap+) (default = usa)
  -name <string>     Application name            (default = none)
  -title <string>    Individual Card Titles      (default = none)
  -dcsize <value>    dcsize (0=long 1=short)     (default = long)
  -fill <value>      fill (0=none 1=filled)      (default = none)
  -save <value>      save (0=no 1=yes)           (default = no)
  -titlemode <value> titlemode (0=short, no individual titles)
                               (1=short, individual card titles)
                               (2=long, no individual titles (default))
                               (3=long, individual card titles)
  -bin               Output bin files             At least one
  -raw               Output raw files             of these options
  -bin               Output bmp files             is required
  -music <value>     music (0=Normal 1=cheery)   (default = normal)
  -help (or -?)      Print extended usage info
```

### nedcenc

```txt
Nintendo eReader Dotcode encoder/decoder v1.4
Copyright 2007 CaitSith2

Usage: ./build/mac/nedcenc [options] [-i] infile [[-o] outfile]

[options]
        -i      In file (required)
        -o      Out file (required)
        -e      Encode bin 2 raw, Outfile required (Default operation)
        -d      Decode raw 2 bin. Outfile required
        -f      Repair raw file
        -s      Dot code signature (encoding only)
                < - Input hex.
                << - Input <
                > - If inputting hex, end hex input, otherwise input >
```

### nedclib2 library (.o / .dll)

#### Docs

Please read the header file in `src/lib/nedclib2.h`

#### Hello, World!

GBA: https://web.archive.org/web/20210514055343/http://users.skynet.be/firefly/gba/download/example/ereader_gba_example_hello_world.zip

Z80: https://web.archive.org/web/20210514055343/http://users.skynet.be/firefly/gba/download/example/ereader_z80_example_hello_world.zip

#### Mario Sprite

GBA: https://web.archive.org/web/20210514055343/http://users.skynet.be/firefly/gba/download/example/ereader_gba_example_mario_sprite.zip

Z80: https://web.archive.org/web/20210514055343/http://users.skynet.be/firefly/gba/download/example/ereader_z80_example_mario_sprite.zip

#### Custom Background

GBA: https://web.archive.org/web/20210514055343/http://users.skynet.be/firefly/gba/download/example/ereader_gba_example_custom_background.zip

Z80: https://web.archive.org/web/20210514055343/http://users.skynet.be/firefly/gba/download/example/ereader_z80_example_custom_background.zip

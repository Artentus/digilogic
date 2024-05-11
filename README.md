# digilogic

- Initially (MVP) just a circuit diagram editor
- With the following features:
    - Wire auto-routing
    - Alignment based snapping (rather than grid based)
    - First class dark mode support
    - Cross platform (Windows, Mac, Linux, iOS, Android)
    - Native C (with some Rust), and light weight
- Inspirations:
    - Issie (github.com/tomcl/issie)
    - Digital Logic Sim (github.com/SebLague/Digital-Logic-Sim)
    - Digital (github.com/hneemann/Digital)
    - LogiSim Evolution (github.com/logisim-evolution/logisim-evolution)

## Building

You'll need rust via rustup, and cmake. Windows you'll need MSVC. You need FreeType too.

### Mac

(You can also follow the linux instructions to avoid XCode and use make.)

```sh
git clone --recurse-submodules https://github.com/rj45/digilogic.git
cd digilogic
mkdir build
cd build
cmake .. -G Xcode -DCMAKE_BUILD_TYPE=Release
cmake --build . --config Release
```

### Windows

You need to install FreeType somehow and then pass the path to cmake.

This might be potential a source: https://github.com/ubawurinna/freetype-windows-binaries

MSVC is also required, as well as cmake.

```sh
git clone --recurse-submodules https://github.com/rj45/digilogic.git
cd digilogic
cmake -B build -DCMAKE_BUILD_TYPE=Release -DFREETYPE_DIR=<path_to_freetype>
cmake --build build --config Release
build\Release\digilogic.exe
```

### Linux X11 (Xorg)

You will need FreeType, cmake and build essentials installed. You may also need dev libraries for X11.

Note: Older versions of FreeType may cause font rendering issues, need to investigate if there is a fix.

```sh
git clone --recurse-submodules https://github.com/rj45/digilogic.git
cd digilogic
mkdir build
cmake .. -DCMAKE_BUILD_TYPE=Release
make
./digilogic
```

### Linux Wayland

Note: For gnome, I recommend using Xwayland and compiling for X11 rather than native wayland. This will give you window decorations. If you don't use gnome, then you won't have this problem and Wayland will work fine for you.

You will need FreeType, cmake and build essentials installed. You may also need dev libraries for Wayland.

```sh
git clone --recurse-submodules https://github.com/rj45/digilogic.git
cd digilogic
mkdir build
cmake .. -DCMAKE_BUILD_TYPE=Release -DUSE_WAYLAND=1
make
./digilogic
```

## License

Apache 2.0, see [NOTICE](./NOTICE) and [LICENSE](./LICENSE).
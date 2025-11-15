Modified by asmwarrior
---------

Clone the latest lunasvg code by the command:
```
git clone git@github.com:asmwarrior/lunasvg.git
```

Then under the MSYS2's MINGW64 shell, run the below command
```
rm -rf build
cmake -B build -DBUILD_SHARED_LIBS=ON -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=./bin .
cmake --build build
cmake --install build
```

Now, the folder `bin` contains the dll files and the header files. So, just copy them to the `liblunasvg` folder, so it looks like as below

```
# tree
.
├── bin
│   ├── liblunasvg.dll
    └── libplutovg.dll
└── include
    ├── lunasvg
    │   └── lunasvg.h
    └── plutovg
        └── plutovg.h

5 directories, 4 files

```

Now, config the Code::Blocks `cbp` file to link to the dll.


About
---------
wxTestSVG2 compares appearance and performance of [NanoSVG](https://github.com/memononen/nanosvg) and [LunaSVG](https://github.com/sammycage/lunasvg),
when used as a rasterization tool for `wxBitmapBundle`.

![wxTestSVG2 Screenshot](wxtestsvg2-screenshot.png?raw=true)

The value of `#define WXSVGTEST2_BENCH_FULL` (in svgbench.cpp) affects what
is benchmarked: 0 means that the benchmark will include only `wxBitmapBundle::ToBitmap()`
times while non-zero means the benchmark will also include time needed for creating
wxBitmapBundle from an in-memory SVG.

Surprisingly, LunaSVG seems consistently noticeably faster when using on popular
icon sets (Tango, Flat Color, Fluent UI, or Material Design; bundled in the SVG folder)
when testing at resolutions expected for GUI icons, regardless of `WXSVGTEST2_BENCH_FULL` value.

Tested only 64-bit release build on Windows with MSVS v17.8.5 and GCC 13.2.

Build Requirements
---------
* CMake v3.24 or newer.
* wxWidgets v3.2.0 or newer.
* LunaSVG is included in the repo (physically, not as a GIT submodule).

Licence
---------
[wxWidgets licence](https://github.com/wxWidgets/wxWidgets/blob/master/docs/licence.txt)
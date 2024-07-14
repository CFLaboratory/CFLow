# CFLow

CFLow (part of the Computational Fluids Laboratory) is a general purpose CFD solver.
A particular goal with `CFLow` is to investigate the use of modern programming techniques for
developing high performance CFD codes that are portable across CPU and accelerated architectures and
scale from laptop/workstations up to supercomuters.

## Building

The `CFLow` buildsystem is based on `cmake` and is initially configured by running
```
cmake -B build .
```
in the project root directory, this will create a `build/` directory containing the configuration and
build information.
After configuring, `CFLow` can be built by running
```
cmake --build build
```

### Requirements

`CFLow` is written in C++, building requires a modern C++ compiler.

Building the documentation (see [Documentation](#doc)) requires `Doxygen`.

## Documentation    {#doc}

Documentation for `CFLow` is available as `.pdf` and `.html` formats produced by `Doxygen` from
source code and documentation sources, including [design](doc/design.md) documentation.
To build the documentation run
```
cmake --build build --target doc
```
which will produce a new directory `man/` containing the documentation.

## License

CFLow is available under the Apache 2.0 License, see the [LICENSE](LICENSE.txt) file.

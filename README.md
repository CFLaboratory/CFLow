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

## Roadmap

A roadmap outlining the plans for `CFLow` v1.0 is available in the [ROADMAP](doc/ROADMAP.md) file.

## License

CFLow is available under the Apache 2.0 License, see the [LICENSE](LICENSE.txt) file.

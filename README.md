# Template For C++ Projects

![C++](https://img.shields.io/badge/C%2B%2B-20-blue)
![License](https://img.shields.io/github/license/pai4451/CppProjectTemplate)
![Ubuntu CI](https://github.com/pai4451/CppProjectTemplate/actions/workflows/ubuntu.yml/badge.svg)
![macOS CI](https://github.com/pai4451/CppProjectTemplate/actions/workflows/macos.yml/badge.svg)
![Windows CI](https://github.com/pai4451/CppProjectTemplate/actions/workflows/windows.yml/badge.svg)
![Docs](https://github.com/pai4451/CppProjectTemplate/actions/workflows/documentation.yml/badge.svg)
![CodeQL](https://github.com/pai4451/CppProjectTemplate/actions/workflows/codeql.yml/badge.svg)

A template for modern C++ projects with CMake, testing, CI/CD, and tooling pre-configured.

## Features

- Library, executable and test code separated in distinct folders
- Modern CMake for building and compiling
- External libraries managed by [CPM](https://github.com/cpm-cmake/CPM.cmake), [Conan](https://conan.io/), or [VCPKG](https://github.com/microsoft/vcpkg)
- Unit testing using [Catch2](https://github.com/catchorg/Catch2) v3
- General purpose libraries: [JSON](https://github.com/nlohmann/json), [spdlog](https://github.com/gabime/spdlog), [cxxopts](https://github.com/jarro2783/cxxopts) and [fmt](https://github.com/fmtlib/fmt)
- Continuous integration with GitHub Actions and [pre-commit](https://pre-commit.com/)
- Code documentation with [Doxygen](https://doxygen.nl/) and [GitHub Pages](https://pai4451.github.io/CppProjectTemplate/)
- Tooling: Clang-Format, CMake-Format, Clang-Tidy, Sanitizers, Code Coverage

## Structure

```text
├── CMakeLists.txt
├── app
│   ├── CMakeLists.txt
│   └── main.cc
├── cmake
│   └── cmake modules
├── docs
│   ├── Doxyfile
│   └── html/
├── external
│   └── CMakeLists.txt
├── src
│   ├── CMakeLists.txt
│   ├── foo/...
│   └── bar/...
└── tests
    ├── CMakeLists.txt
    └── test_*.cc
```

Library code goes into [src/](src/), main program code in [app/](app) and tests go in [tests/](tests/).

## Requirements

- CMake 3.22+
- GNU Makefile
- Doxygen (optional, for docs)
- MSVC 2019+, GCC 10+, or Clang 12+
- gcovr (optional, for code coverage)

## Building

Clone the repo:

```shell
git clone --recurse-submodules https://github.com/pai4451/CppProjectTemplate
```

**App Executable**

```shell
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release --target main
./build/app/main
```

**Unit Testing**

```shell
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug
cmake --build build --config Debug
ctest --test-dir build --output-on-failure
```

**Documentation**

```shell
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug
cmake --build build --config Debug --target docs
```

**Code Coverage (Unix only)**

```shell
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug -DENABLE_COVERAGE=On
cmake --build build --config Debug --target coverage -j4
```

For more info about CMake see [here](./README_cmake.md).

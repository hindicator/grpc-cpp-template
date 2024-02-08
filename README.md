# grpc-cpp-template

This repository contains a gRPC C++ example with a continuous integration (CI) job. It demonstrates how to set up a simple gRPC server and client in C++ and how to build and test it using GitHub Actions.

## Structure

The repository is structured as follows:

- [`.github/workflows/test-packages.yml`](command:_github.copilot.openRelativePath?%5B%22.github%2Fworkflows%2Ftest-packages.yml%22%5D ".github/workflows/test-packages.yml"): This is the GitHub Actions workflow file that sets up the CI job. It checks out the code, sets up the necessary packages, builds the gRPC C++ example, and runs tests.
- [`cmake/common.cmake`](command:_github.copilot.openRelativePath?%5B%22cmake%2Fcommon.cmake%22%5D "cmake/common.cmake"): This file contains common CMake commands used in the project.
- [`example/`](command:_github.copilot.openRelativePath?%5B%22example%2F%22%5D "example/"): This directory contains the gRPC C++ example code, including the server (`greeter_server.cc`), client (`greeter_client.cc`), and the protobuf definition (`helloworld.proto`).
- [`example/CMakeLists.txt`](command:_github.copilot.openRelativePath?%5B%22example%2FCMakeLists.txt%22%5D "example/CMakeLists.txt"): This file contains the CMake commands to build the gRPC C++ example.

## Building the Project

The project is built using CMake. The build process is automated in the GitHub Actions workflow defined in [`.github/workflows/test-packages.yml`](command:_github.copilot.openSymbolInFile?%5B%22.github%2Fworkflows%2Ftest-packages.yml%22%2C%22.github%2Fworkflows%2Ftest-packages.yml%22%5D ".github/workflows/test-packages.yml").

The build steps in the workflow are:

1. Check out the code.
2. Set up the necessary packages.
3. Set up gRPC using the `hindicator/grpc-setup@v1` action.
4. Build the gRPC C++ example.

## Instructions

You can find a complete set of instructions for building gRPC in [C++ Quick Start][].

**Note**: make sure to install using `-DCMAKE_INSTALL_PREFIX="<your_installation_path>"`.

**Example**:
```
cmake -DgRPC_INSTALL=ON \                    
      -DgRPC_BUILD_TESTS=OFF \
      -DCMAKE_INSTALL_PREFIX="~/grpc" \
      -DBUILD_SHARED_LIBS=ON \
      ..
```

After installing gRPC on your local machine,
run the following commands :
```
# export GRPC_ROOT="<your_installation_path>"
export GRPC_ROOT="~/grpc"
cd example
mkdir -p build
cd build
cmake -DCMAKE_PREFIX_PATH="$GRPC_ROOT" ..
make
```


[C++ Quick Start]: https://grpc.io/docs/languages/cpp/quickstart


## Running the Example

The example consists of a gRPC server and client. The server implements the `Greeter` service defined in [`example/helloworld.proto`](command:_github.copilot.openSymbolInFile?%5B%22example%2Fhelloworld.proto%22%2C%22example%2Fhelloworld.proto%22%5D "example/helloworld.proto"). The client sends a `HelloRequest` to the server and receives a `HelloReply`.

For more detailed instructions on building and running the example, see the gRPC C++ Hello World Example in the [`example/`](command:_github.copilot.openRelativePath?%5B%22example%2F%22%5D "example/") directory.

## Contributing

Contributions are welcome. Please make sure to test your changes by running the GitHub Actions workflow before submitting a pull request.

## License

This project is licensed under the Apache License, Version 2.0. See the LICENSE file for details.
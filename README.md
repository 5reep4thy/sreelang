# SREELANG
A toy language to get a hands on with LLVM.

To build run - 

```
mkdir build-sreelang
cmake -G Ninja -DCMAKE_BUILD_TYPE=Debug -DLLVM_DIR=<path-to-llvm-lib>  -DCMAKE_INSTALL_PREFIX=. .
ninja
ninja install
```
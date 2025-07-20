# SREELANG
A toy language to get a hands on with LLVM.

To build run - 

```
mkdir build-sreelang
cmake -G Ninja -DCMAKE_BUILD_TYPE=Debug -DLLVM_DIR=<path-to-llvm-lib>  -DCMAKE_INSTALL_PREFIX=. .
ninja
ninja install
```

Issues run into in MacOS_arm64 - 
The builtin libzstd.dylib is for x86_64 (rosetta) and we have to build zstd for arm64 and replace it.
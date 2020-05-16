## WASM Toolchain

### [Emscripten](https://hub.docker.com/repository/docker/mziyabo/emscripten)
Toolchain image for [Emscripten](https://emscripten.org/), a source-to-source compiler that runs as a back end to the LLVM compiler.

**Usage**:
Create hello.cpp and compile to hello.wasm
``` PowerShell
New-item hello.cpp -Value "#include <iostream>
using namespace std;
int main() {
  cout << `"Hello World`" << endl;
}"

docker run --rm -v $pwd`:/target mziyabo/emscripten emcc ./hello.cpp -o hello.wasm
```

### [Wasmtime](https://hub.docker.com/repository/docker/mziyabo/wasmtime)
Executable image for [Wasmtime](https://wasmtime.dev/), a JIT-style runtime for WebAssembly.

**Usage** 

Execute ./hello.wasm in wasmtime
``` powershell
docker run --rm -v ${pwd}:/target mziyabo/wasmtime ./hello.wasm
```

### Known Issues
- Emscripten image is a little beefy
- Might need to address adding link library and includes directories
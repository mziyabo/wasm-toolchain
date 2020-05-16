## WASM Toolchain

### [Emscripten](https://hub.docker.com/repository/docker/mziyabo/emscripten)
[Emscripten](https://emscripten.org/) toolchain Image

**Usage**:
Create hello.cpp and compile to hello.wasm
``` PowerShell
New-item hello.cpp -Value "#include <iostream>
using namespace std;
int main() {
  cout << `"Hello World`" << endl;
}"

docker run --rm -v $pwd`:/target mziyabo/emscripten emcc ./hello.cpp
```


### [Wasmtime](https://hub.docker.com/repository/docker/mziyabo/wasmtime)
Executable image for [Wasmtime](https://wasmtime.dev/), a JIT-style runtime for WebAssembly.

**Usage** PowerShell:
Create hello.rs file and compile to wasm
``` powershell
New-Item hello.rs -Value  "fn main() {
 println!(`"Hello`");
}"

rustc --target=wasm32-wasi hello.rs
``` 

Execute ./hello.wasm in wasmtime
``` powershell
docker run --rm -v ${pwd}:/target mziyabo/wasmtime ./hello.wasm
```
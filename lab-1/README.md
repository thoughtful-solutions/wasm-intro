# Lab-1

## Configure the environment

ensure go compile in in place
```
which go
go version
```

ensure that  WebAssembly Runtime is present 

```
which wasmtime
```


## Create a simple hello world program in go

```
cat <<EOF >hello.go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
EOF
```


## Compile the code

### Native compile 

```
go build hello.go
chmod +x hello
./hello
```
or in Windows
```
go build -o hello.exe hello.go
hello.exe
```

and the output will be

```
Hello, World!
```

### WASM Compile WASM Runtime (wasmtime)

```
set GOOS=wasip1
set GOARCH=wasm
go build -o hello-wasi.wasm hello.go
wasmtime hello-wasi.wasm
```

and the output will be

```
Hello, World!
```

### WASM Compile Browser Runtime

```
set GOOS=js
set GOARCH=wasm
go build -o hello-browser.wasm hello.go
```

This requires an HTML file to get this to run
```
<html>
<head>
    <script src="wasm_exec.js"></script>
    <script>
        const go = new Go();
        WebAssembly.instantiateStreaming(fetch("hello-browser.wasm"), go.importObject).then((result) => {
            go.run(result.instance);
        });
    </script>
</head>
</html>
```

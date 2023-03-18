# WASM Pack Setup
This is a template for a Rust library that is compiled to WebAssembly. It uses [wasm-pack](https://rustwasm.github.io/wasm-pack/installer/#) to build the library and [wasm-bindgen](https://rustwasm.github.io/docs/wasm-bindgen/) to generate the JavaScript bindings.

## Setup
1. Ensure you have [Rust](https://www.rust-lang.org/tools/install) installed
2. Install [wasm-pack](https://rustwasm.github.io/wasm-pack/installer/#)
3. Create a new Rust library with `cargo new --lib <name>`
4. Add wasm-bindgen to your dependencies in `Cargo.toml`. For example: `cargo add wasm-bindgen`
5. Specify lib as a crate type in `Cargo.toml`. For example: `crate-type = ["cdylib"]`
6. Add the following to your `lib.rs` file:
```rust
use wasm_bindgen::prelude::*;

#[wasm_bindgen]
pub fn add(a: i32, b: i32) -> i32 {
    a + b
}
```
7. Run `wasm-pack build --target web` to build the library
8. Create a new HTML file. Amd import the generated JavaScript file. For example:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>WASM Setup Example</title>

</head>

<body>
    <script type="module">
        import init, { add } from './pkg/wasm_pack_setup.js';
        await init();
        console.log(add(1, 2));
    </script>
</body>

</html>
```
1. Ensure you have the python web server installed. If not, run `pip install http-server`
2. Run `python3 -m http.server` to start a local server
3.  Open `http://localhost:8000` in your browser
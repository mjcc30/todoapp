# todoapp

## install rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
export PATH="$HOME/.cargo/bin:$PATH"

## install wasm
cargo install wasm-bindgen-cli
rustup target add wasm32-unknown-unknown

## create lib wasm
cargo new --lib wasm

## build lib
cargo build --lib --target wasm32-unknown-unknown

## install aleph
deno install --unstable -A -f -n aleph https://deno.land/x/aleph@v0.2.28/cli.ts

## init aleph project
aleph init todoapp

## link to server
wasm-bindgen --target deno ./target/wasm32-unknown-unknown/debug/wisesayings.wasm --out-dir ../todoapp/wasm

## start aleph
aleph dev


# Ressource
https://alephjs.org/docs/get-started
https://thenewstack.io/using-web-assembly-written-in-rust-on-the-server-side/
https://www.youtube.com/watch?v=SDTedmFhnQc
https://github.com/reselbob/wisesayingswasm

# Rust staticlib musl test project

In this project I'm trying to compile a staticlib with musl and install that
with a Ruby gem.

## Usage

`./run build` will compile the Rust staticlib with musl on debian using
[clux/muslrust](https://github.com/clux/muslrust/)'s docker image.

After compilation it will use the compiled staticlib and move that to an Alpine
linux container [ruby:2.3.1-alpine](https://hub.docker.com/_/ruby/) and try to
install it there in a Ruby gem.

`./run clean` will remove all `target` directories and caches.

## Note on fork

Project based on
[steveklabnik/rust_example](https://github.com/steveklabnik/rust_example).

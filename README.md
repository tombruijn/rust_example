# Rust staticlib musl test project

In this project I'm trying to compile a staticlib with musl and install that
with a Ruby gem.

## Usage

`./run build` will compile the Rust staticlib with musl on debian using
[clux/muslrust](https://github.com/clux/muslrust/)'s docker image.

After compilation it will move the compiled staticlib to an Alpine linux
container [ruby:2.3.1-alpine](https://hub.docker.com/_/ruby/) and try to
install it in a Ruby gem.

`./run clean` will remove all `target` directories and caches.

## Result

Building the staticlib seems to go fine, but once it's trying to be installed
in the Ruby gem the following error is thrown:

```
$ ruby extconf.rb
checking for rust_example_init() in -lrust_example... yes
creating Makefile
$ make clean
$ make
compiling rust_example.c
linking shared-object rust_example/rust_example.so
/usr/lib/gcc/x86_64-alpine-linux-musl/5.3.0/../../../../x86_64-alpine-linux-musl/bin/ld: ./librust_example.a(__stdout_write.lo): relocation R_X86_64_PC32 against protected symbol `__stdio_write' can not be used when making a shared object
/usr/lib/gcc/x86_64-alpine-linux-musl/5.3.0/../../../../x86_64-alpine-linux-musl/bin/ld: final link failed: Bad value
collect2: error: ld returned 1 exit status
Makefile:254: recipe for target 'rust_example.so' failed
make: *** [rust_example.so] Error 1
```

## Note on fork

Project based on
[steveklabnik/rust_example](https://github.com/steveklabnik/rust_example).

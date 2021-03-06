# Rust
## Installation
```
Install
$ curl https://sh.rustup.rs -sSf | sh
$ vi ~/.bash_profile
    add the following:
        export PATH=$HOME/.cargo/bin:$PATH
$ source ~/.bash_profile

Check
$ rustc --version
$ rustup --version
$ cargo --version
```

```
If curl don't work
(get
dyld: Library not loaded: @rpath/libssl.1.0.0.dylib)
$ conda install libssh2
```

## Construct developing environment
```
To complete code, use Racer.

Instal Rust of nightly version
$ brew install sdl2
$ rustup update
$ rustup override set nightly
$ rustup update nightly

Install Racer
$ cargo install racer

Get Rust source 
$ rustup toolchain add nightly
$ rustup component add rust-src
$ vi ~/.bash_profile
    add the following:
        export RUST_SRC_PATH="$(rustc --print sysroot)/lib/rustlib/src/rust/src"
$ source ~/.bash_profile

Check working
$ racer complete std::io::B 

Two ways to complete Rust on Vim are shown.
1) with vim-racer
$ vi ~/.config/nvim/dein.toml
    add the following:
        [[plugins]]
        repo = 'racer-rust/vim-racer'
        on_ft = ['rust']
        hook_add = '''
          set hidden
          let g:racer_cmd = "~/.cargo/bin/racer"
          let g:racer_experimental_completer = 1
          let g:racer_insert_paren = 1
        '''

2) With Deoplete

To combine Racer with Deoplete, Rust source code is needed.
Download it.
$ cd ~/programs/othermade/sources/
$ git clone --depth=1 https://github.com/rust-lang/rust.git

$ vi ~/.config/nvim/dein.toml
    add the following:
        [[plugins]]
        repo = 'sebastianmarkow/deoplete-rust'
        depends = ['Shougo/deoplete.nvim']
        on_ft = ['rust']
        hook_add = '''
          let g:deoplete#sources#rust#racer_binary='~/.cargo/bin/racer'
          let g:deoplete#sources#rust#rust_source_path='~/programs/othermade/sources/rust/src'
          let g:deoplete#sources#rust#show_duplicates=1
          let g:deoplete#sources#rust#disable_keymap=1
          let g:deoplete#sources#rust#documentation_max_height=20
        '''

[ref] https://github.com/sebastianmarkow/deoplete-rust

```

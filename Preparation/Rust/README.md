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
To install Racer which uses functions of nightly version
$ brew install sdl2
$ rustup update
$ rustup override set nightly
$ rustup update nightly

$ cargo install racer

1) With Deoplete
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

see https://github.com/sebastianmarkow/deoplete-rust

2) with vim-racer
```

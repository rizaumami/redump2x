[xdvdfs](https://github.com/antangelo/xdvdfs) is an original Xbox DVD Filesystem library and management tool.


# How to

## 1. Download Releases

Go to https://github.com/antangelo/xdvdfs/releases/latest to download the latest relese.

## 2. Build

```sh
sudo apt install cargo
git clone https://github.com/antangelo/xdvdfs
cd xdvdfs
cargo build --release
```

Generated binary would be in `target/release` folder.

Use the following `cargo.toml` to generated smaller binary:
```toml
[profile.release]
lto = true
strip = true
opt-level = "z"
codegen-units = 1
panic = "abort"
```

### 3. Install from [crates.io](https://crates.io/)

```sh
sudo apt install cargo
cargo install xdvdfs-cli
```

All binaries installed with `cargo install` are stored in the installation root's bin folder. \
If you installed Rust using `rustup.rs` and don't have any custom configurations, this directory will be `$HOME/.cargo/bin`. \
Ensure that directory is in your `$PATH` to be able to run programs you've installed with `cargo install`.
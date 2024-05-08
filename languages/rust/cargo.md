1. `cargo new` 新建一个rust项目
2. `cargo build` 编译rust项目
3. `cargo run` 编译 + 运行
4. `cargo check` 检查能否编译通过, 更快

# 1 cargo build

第一次运行`cargo build` 会在项目顶层目录生成一个`cargo.lock`文件。该文件用来跟踪当前项目所依赖库的精确版本。

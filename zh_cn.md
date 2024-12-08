# Mc-Router
一个基于域名的 Minecraft 反向代理。

本项目基于 https://github.com/JavaDerg/mc-router 发布，其许可遵循 GPL-3 许可证。

## 什么是 Mc-Router
如果你有多个 Minecraft 服务器在运行，但只有有限数量的端口，这个工具适合你。
Mc-Router 允许你在单个端口上监听，并为多个本地 Minecraft 服务器进行代理，具体根据连接时使用的域名进行转发。

## 为什么使用 Mc-Router
因为我懒得设置正确的 DNS 记录，让 Minecraft 能够识别正确的端口 :)

## 构建步骤
1. 确保你安装了最新版本的 Rust 和 Cargo，可以通过 `rustup update` 来更新；如果你还没有安装 `rustup`，可以在 [这里](https://rustup.rs/) 获取。
2. 克隆该仓库并进入目录。
3. 运行 `cargo build --release`。
4. 你会在 `target/release/mc-router` 找到编译好的可执行文件（在 Windows 上需添加 `.exe` 后缀）；

## 使用方法
1. 创建一个配置文件，类似于 [example.json](example.json) 中展示的格式。
   服务器将尝试从你的环境变量中获取配置路径，具体是 `MCR_CONFIG`。 （默认为 `./mcr.json`）

   此外，你还可以使用 `MCR_INTERFACE` 提供服务器应监听的接口/端口。（默认为 `0.0.0.0:25565`）

   设置此环境变量以切换为ipv6 `USE_IPV6=true`（默认为`false`）

   设置此环境变量以启用日志打印 `RUST_LOG=info`（默认不打印任何内容）

2. 运行服务器。

    例如，你可以这样运行

    ```sh
    USE_IPV6=true RUST_LOG=info ./mc-router
    ```

#### 注意事项：
- 配置会自动热加载，无需重启服务器，重启会导致所有当前用户断开连接。

## 更改记录

- 支持了mc高版本运行（大概）
- 支持了ipv6
- 支持了默认转发
- 修改了 README

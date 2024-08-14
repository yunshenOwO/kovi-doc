# 监听事件

通过 PluginBuilder 可以监听事件

[[toc]]

## plugin.on_msg()

添加消息监听函数, 包括好友私聊、群消息以及讨论组消息

需传入一个闭包，闭包类型为 `Fn(&AllMsgEvent) + Send + Sync + 'static`

```rust
#[kovi::plugin] 
pub fn main(mut plugin: PluginBuilder) {
    plugin.on_msg(move |event| {// [!code focus]
        event.reply("Hi!") // [!code focus]
    });// [!code focus]
}
```

## plugin.on_admin_msg()

添加管理员消息监听函数, 包括好友私聊、群消息以及讨论组消息，Kovi会帮你筛选消息。

需传入一个闭包，闭包类型为 `Fn(&AllMsgEvent) + Send + Sync + 'static`

```rust
#[kovi::plugin] 
pub fn main(mut plugin: PluginBuilder) {
    plugin.on_admin_msg(move |event| {// [!code focus]
        event.reply("Hi!") // [!code focus]
    });// [!code focus]
}
```


## plugin.on_all_notice()

添加 OneBot 的 `通知事件` 监听函数。

需传入一个闭包，闭包类型为 `Fn(&AllNoticeEvent) + Send + Sync + 'static`

```rust
#[kovi::plugin] 
pub fn main(mut plugin: PluginBuilder) {
    plugin.on_all_notice(|event| { // [!code focus]
        println!("{}", event.notice_type); // [!code focus]
    }); // [!code focus]
}
```
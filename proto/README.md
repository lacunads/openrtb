# OpenRTB Protobuf

本目录中的 `openrtb.proto` 是 OpenRTB 2.5.0 的完整、规范 Protobuf 定义。

- 协议版本：OpenRTB 2.5.0
- 语法版本：Protocol Buffers proto2
- 来源：IAB Tech Lab `openrtb-proto-v2`
- 基线提交：`1eab411022342a6144fe955cc3f156b7a43f514d`
- 基线标题：`OpenRTB proto v2.5.0`

## 文件说明

- `openrtb.proto`：唯一规范定义，包含 BidRequest、BidResponse、Native 1.2
  请求/响应、全部核心对象和枚举。
- `request.proto`：兼容入口，使用 `import public "openrtb.proto"` 导出请求相关类型。
- `response.proto`：兼容入口，使用 `import public "openrtb.proto"` 导出响应相关类型。

兼容入口不会复制消息定义，因此不会产生字段编号或枚举值漂移。新代码建议直接引用
`openrtb.proto`；已有构建脚本可以继续引用 `request.proto` / `response.proto`。

HTTP/JSON 对接时仍以 OpenRTB 2.5 的 JSON 字段语义为准。官方 Protobuf 映射会把部分
JSON `0/1` 标志表示为 `bool`（如 `test`、`allimps`、`source.fd`、`regs.coppa`），
并把部分 JSON 数字枚举表示为 Protobuf enum；这是二进制建模差异，不改变 JSON 协议值。

## 编译验证

在项目根目录运行：

```bash
protoc --proto_path=proto \
  --descriptor_set_out=/tmp/openrtb.desc \
  proto/openrtb.proto proto/request.proto proto/response.proto
```

OpenRTB 2.5 原始定义中 `ContentCategory` 的部分历史枚举名称（如 `IAB11` 与
`IAB1_1`）在忽略大小写并去掉枚举前缀后会发生命名冲突，`protoc` 可能给出 warning。
这些名称属于上游协议的历史兼容数据，不应在本项目中擅自重命名。

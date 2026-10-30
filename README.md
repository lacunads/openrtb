## 说明
本文档是AdExchange-Publiser的对接说明。对接协议采用openrtb 2.5协议。

中文文档请求参考 AdExchange-Publisher接入文档.md

英文文档请参考EN RTB-Integration.md

examples目录包含了native、banner和Video的请求和响应示例。

## Protobuf 协议定义

`proto/openrtb.proto` 是 OpenRTB 2.5.0 的规范定义，字段名称、类型、基数和字段编号以
IAB Tech Lab `openrtb-proto-v2` 的 `OpenRTB proto v2.5.0` 提交
`1eab411022342a6144fe955cc3f156b7a43f514d` 为基线。

`proto/request.proto` 和 `proto/response.proto` 保留为兼容入口，通过
`import public "openrtb.proto"` 重新导出同一套完整类型。生成代码时建议直接编译
`proto/openrtb.proto`；需要保留旧入口时，可将三个文件一起编译。

```bash
protoc --proto_path=proto \
  --descriptor_set_out=openrtb.desc \
  proto/openrtb.proto proto/request.proto proto/response.proto
```

## Description
This document is the instructions of AdExchanget-publisher， which is based on openrtb 2.5 protocol.

For Chinese documents，please refer to AdExchange-Publisher接入文档.md

For English documents, please refer to EN RTB-Integration.md

The examples directory contains request and response examples for native 、 banner and Video.

## Protobuf schema

`proto/openrtb.proto` is the canonical OpenRTB 2.5.0 schema. Its field names,
types, cardinality, and field numbers are based on the IAB Tech Lab
`openrtb-proto-v2` commit `1eab411022342a6144fe955cc3f156b7a43f514d`
(`OpenRTB proto v2.5.0`).

`proto/request.proto` and `proto/response.proto` remain compatibility entry
points and re-export the same complete schema through
`import public "openrtb.proto"`. Generate from `proto/openrtb.proto` directly,
or compile all three files when the legacy entry points are required.

```bash
protoc --proto_path=proto \
  --descriptor_set_out=openrtb.desc \
  proto/openrtb.proto proto/request.proto proto/response.proto
```

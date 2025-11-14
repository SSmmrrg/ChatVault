<div align="center">

# ChatValut
## 根据开源形目chatlog以及wxkey开发而来

_聊天记录工具，帮助大家轻松使用自己的聊天数据_

</div>

## Feature   # #特性

- 从本地数据库文件中获取聊天数据
- 支持Windows增加兼容微信4.0及以上版本
- 支持数据密钥获取
- 支持自动解密与新消息 Webhook 回调
- 新增GUI，支持命令行与 HTTP API 服务
- 支持 MCP Streamable HTTP，便于与 AI 助手集成
- 支持多账号管理与切换

## Quick Start   ##快速入门

### 基本步骤

1. 下载ChatVault到本地
2. 运行程序：执行 `.\chatvault.exe gui` 启动 GUI
3. 解密数据：选择 `解密数据`
4. 开启 HTTP 服务：选择 `开启 HTTP 服务`
5. 访问数据：通过 HTTP API 或 MCP 集成访问聊天记录
`
提示：如果电脑端微信聊天记录不全，可从手机端迁移数据；见下文.

### 常见问题快速解决
- 集成 AI 助手：参考 MCP 集成
- 无法获取密钥：参考 FAQ（原项目的 Issue 说明）

## 安装与构建

### 预编译版本

可参考项目 Releases 页面下载对应平台的预编译版本 `chatvault`。

## 使用指南

将chatvault下载到本地之后在所子啊目录打开终端输入 ` .\chatvault.exe gui`


### 数据目录定位

Windows：   窗口:

```
# 微信 3.x
C:\Users\{用户名}\Documents\WeChat Files\{微信ID}

# 微信 4.x
C:\Users\{用户名}\Documents\xwechat_files\{微信ID}
```

## HTTP API

启动后默认地址 `http://127.0.0.1:5030`。

示例：

```
GET /api/v1/chatlog?time=2023-01-01&talker=wxid_xxx拿/ api / v1 / chatlog ?时间= 2023-01-01&talker = wxid_xxx
```

参数：`time`，`talker`，`limit`，`offset`，`format`（json/csv/text）。

其他：`/api/v1/contact`、`/api/v1/chatroom`、`/api/v1/session`。

多媒体：`/image/<id>`、`/video/<id>`、`/file/<id>`、`/voice/<id>`、`/data/<relative path>`。多媒体:“/图像/ < id > ', ' /视频/ < id > ', ' /文件/ < id > ', ' /声音/ < id > ', ' /数据/ <相对路径> '。

## Webhook   Webhook # #

开启自动解密后，可通过 HTTP POST 推送消息到指定 URL。支持 host 配置与监听多个会话。可用 `CHATLOG_WEBHOOK` 环境变量配置。

## MCP 集成

支持 MCP Streamable HTTP，客户端可直接对接 `http://127.0.0.1:5030/mcp`。对不支持的客户端可通过 mcp-proxy 转发。

## 安全与发布

- 构建加固：建议使用 `garble build` 进行符号/字符串混淆；不影响正常运行。
- 去符号与路径：`-w -s` 与 `-trimpath` 已启用，减小体积、移除调试信息。
- 反调试轻量检测：在关键路径加入调试器检测与随机延迟，提升对抗性且不影响使用。
- 代码签名：建议对 Windows 可执行文件进行 Authenticode 签名，提升可信度与防篡改。

## 从手机迁移聊天记录

手机微信：我 → 设置 → 通用 → 聊天记录迁移与备份 → 迁移到电脑。完成后使用 ChatVault 获取密钥并解密数据。

## 免责声明

仅处理自己合法拥有或已获授权的数据；严禁用于未经授权获取、查看或分析他人记录；开发者不对任何损失负责；使用第三方 LLM 服务须遵守其条款与隐私政策。

## License   # #许可证

基于 Apache-2.0 许可证开源。

## 隐私政策

本项目不收集任何用户数据；所有处理在本地进行。使用第三方服务请遵守其隐私政策。

## Thanks   # #谢谢

- wechat-dump-rs、PyWxDump 等社区项目
- chatlog原项目作者
- wx_key作者大佬
- MCP 协议与各开源库贡献者

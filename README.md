# QwenPaw HarmonyOS APP

<p align="center">
  <img src="https://img.shields.io/badge/ArkTS-5.0.0-007AFF?logo=huawei" alt="ArkTS"/>
  <img src="https://img.shields.io/badge/OpenHarmony-API%2023-FF6A00?logo=huawei" alt="OpenHarmony"/>
  <img src="https://img.shields.io/badge/DevEco-Studio%205-007AFF?logo=huawei" alt="DevEco"/>
  <img src="https://img.shields.io/github/license/R3lyW1nd/QwenPaw-HarmonyOS-APP" alt="License"/>
</p>

<p align="center">
  <b>让你的 QwenPaw Agent 随身而行</b> —— 原生鸿蒙客户端，基于 ArkTS + ArkUI 开发，完美适配鸿蒙生态。
</p>

---

> ⚠️ **APP 目前正在开发中，尽请期待！**

---

## 目录

- [功能特性](#-功能特性)
- [技术栈](#-技术栈)
- [项目架构](#-项目架构)
- [使用说明](#-使用说明)
- [API 对接说明](#-api-对接说明)
- [注意事项](#-注意事项)
- [许可证](#-许可证)

---

## 功能特性

| 功能 | 说明 |
|------|------|
| 实时对话 | SSE 流式响应，打字机效果实时显示 AI 回复 |
| 多 Agent 切换 | 支持切换不同智能体角色 |
| 文件管理 | 查看 / 下载工作空间文件 |
| 数据统计 | Token 消耗统计、API 调用次数追踪 |
| 主题系统 | 浅色 / 深色 / 跟随系统 + 6 种强调色 |
| 多设备协同 | 支持鸿蒙超级终端跨设备流转 |
| 原子化服务 | 一键拉起 Service Widget，免安装快速体验 |
| 智能卡片 | 桌面万能卡片展示对话状态 |
| 鸿蒙通知 | 系统级通知推送 AI 回复完成提醒 |
| 离线缓存 | 消息本地持久化存储，断网可查看 |
| 全局搜索 | 关键词搜索历史消息 |

## 技术栈

| 类别 | 技术 |
|------|------|
| 语言 | ArkTS 5.0.0 (TypeScript 方言) |
| UI 框架 | ArkUI 声明式 UI |
| 架构 | MVVM + 分层架构 |
| 网络层 | @ohos.net.http |
| SSE 流式解析 | @ohos.net.http on('dataReceive') + on('dataEnd') |
| 状态管理 | @State / @Prop / @Link / @Provide + @Consume |
| 本地持久化 | @ohos.data.preferences + 关系型数据库 |
| 主题引擎 | @StorageProp + 资源限定符 |
| 系统集成 | Service Widget / Form Kit / Notification Kit |
| 最低 API | OpenHarmony API 23 |
| 构建工具 | hvigor 6.24.2 + DevEco Studio 5 |

## 项目架构

```
QwenPaw-OH/
├── entry/
│   └── src/
│       └── main/
│           ├── ets/
│           │   ├── pages/
│           │   │   ├── Index.ets                   # 主页（底部导航栏）
│           │   │   ├── ChatPage.ets                # 聊天页
│           │   │   ├── AgentPage.ets               # Agent 管理页
│           │   │   ├── ManagePage.ets              # 管理页（文件/任务）
│           │   │   ├── StatsPage.ets               # 数据统计页
│           │   │   └── SettingsPage.ets            # 设置页
│           │   ├── components/
│           │   │   ├── MessageBubble.ets           # 消息气泡组件
│           │   │   ├── InputBar.ets                # 输入栏组件
│           │   │   ├── ShimmerLoading.ets          # 骨架屏组件
│           │   │   ├── EmptyState.ets              # 空状态组件
│           │   │   └── ThemeSelector.ets           # 主题选择器
│           │   ├── services/
│           │   │   ├── ApiService.ets              # API 层
│           │   │   ├── SseParser.ets               # SSE 流式解析
│           │   │   ├── AuthService.ets             # 认证管理
│           │   │   └── CacheService.ets            # 缓存服务
│           │   ├── models/
│           │   │   ├── Message.ets                 # 消息模型
│           │   │   ├── AgentInfo.ets               # Agent 信息模型
│           │   │   ├── TokenStats.ets              # Token 统计
│           │   │   ├── WorkspaceFile.ets           # 文件模型
│           │   │   └── CronJob.ets                 # 定时任务模型
│           │   └── utils/
│           │       ├── Logger.ets                  # 日志工具
│           │       ├── Formatter.ets               # 格式化工具
│           │       └── Constants.ets               # 常量定义
│           ├── resources/
│           │   ├── base/
│           │   │   ├── element/
│           │   │   │   ├── color.json              # 主题色定义
│           │   │   │   └── string.json             # 字符串资源
│           │   │   └── media/
│           │   │       └── app_icon.png            # 应用图标
│           │   └── dark/                           # 深色主题资源
│           │       └── element/
│           │           └── color.json
│           └── module.json5                        # 模块配置
├── widget/                                         # 桌面卡片模块
│   └── src/
│       └── main/
│           └── ets/
│               └── WidgetCard.ets                  # 万能卡片
├── AppScope/
│   └── app.json5                                   # 应用配置
├── build-profile.json5                             # 构建配置
├── hvigorfile.ts                                   # hvigor 入口
└── README.md
```

## 使用说明

### 下载安装

> 待上架华为应用市场后可通过 AppGallery 下载。

### 首次使用

1. 安装后打开应用
2. 在设置页填写 QwenPaw 服务器地址
3. 输入用户名和密码完成登录
4. 开始与 AI 对话

### 聊天

1. 在底部输入框输入消息，点击发送
2. AI 回复以 SSE 流式实时展示
3. 支持工具调用结果自动展示

### 鸿蒙特色功能

- **万能卡片**：在桌面添加服务卡片，快速查看最近对话
- **超级终端**：支持手机、平板、折叠屏多端协同
- **原子化服务**：无需安装完整应用，通过卡片直接体验核心功能
- **鸿蒙通知**：AI 回复完成后通过系统通知提醒
- **折叠屏适配**：自适应折叠态/展开态布局


## 截图预览

<div align="center">

| | | | |
|---|---|---|---|
<img src='https://raw.githubusercontent.com/R3lyW1nd/QwenPaw-Android-APP/main/screenshots/screenshot_1.jpg' width='170'/> | <img src='https://raw.githubusercontent.com/R3lyW1nd/QwenPaw-Android-APP/main/screenshots/screenshot_2.jpg' width='170'/> | <img src='https://raw.githubusercontent.com/R3lyW1nd/QwenPaw-Android-APP/main/screenshots/screenshot_3.jpg' width='170'/> | <img src='https://raw.githubusercontent.com/R3lyW1nd/QwenPaw-Android-APP/main/screenshots/screenshot_4.jpg' width='170'/> |
<img src='https://raw.githubusercontent.com/R3lyW1nd/QwenPaw-Android-APP/main/screenshots/screenshot_5.jpg' width='170'/> | <img src='https://raw.githubusercontent.com/R3lyW1nd/QwenPaw-Android-APP/main/screenshots/screenshot_6.jpg' width='170'/> | <img src='https://raw.githubusercontent.com/R3lyW1nd/QwenPaw-Android-APP/main/screenshots/screenshot_7.jpg' width='170'/> | |

</div>


## API 对接说明

应用对接 QwenPaw RESTful API，完整文档请参考 [QwenPaw RESTful API 文档](https://qwenpaw.agentscope.io/docs/api-tutorial)。

### 主要接口

| 接口 | 方法 | 说明 |
|------|------|------|
| /api/auth/login | POST | 用户登录认证 |
| /api/console/chat | POST | SSE 流式聊天消息 |
| /api/agents | GET | 获取 Agent 列表 |
| /api/sessions | GET | 获取会话列表 |
| /api/skills | GET | 获取可用技能 |
| /api/tools | GET | 获取可用工具 |
| /api/token/stats | GET | Token 使用统计 |
| /api/workspace/files | GET | 工作空间文件列表 |

### 认证方式

```
Authorization: Bearer <JWT_TOKEN>
```

### SSE 流式响应

聊天接口采用 SSE 协议，通过 `@ohos.net.http` 的 `on('dataReceive')` 和 `on('dataEnd')` 事件实现流式展示。

## 注意事项

1. 应用使用 HTTP 明文传输，请仅在可信网络环境中使用
2. 登录信息通过 Preferences 本地加密存储
3. SSE 连接超时设置为 5 分钟
4. 万能卡片需要 OpenHarmony API 23+
5. 超级终端协同需要登录同一华为账号

## 许可证

MIT License © 2026 R3lyW1nd

---

<p align="center">
  Made with ❤️ by R3lyW1nd &amp; GeoS4C
</p>

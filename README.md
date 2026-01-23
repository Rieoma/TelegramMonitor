# TelegramMonitor

> 🚀 一个高性能的 Telegram 关键词监听 / 检测机器人，支持多群、多关键词、实时推送，适合情报收集、舆情监控与自动化通知场景。接开发 Tg:@Uk233 @DinBoCsbot

---

## ✨ 项目简介

**TelegramMonitor** 是一个基于 Telegram Bot API / MTProto 的监听机器人，用于：

* 监听 **Telegram 群组 / 频道** 消息
* 按 **关键词规则** 实时检测
* 命中后 **自动推送通知**
* 支持云端部署，稳定运行

适用于：

* TG 关键词监控
* 信息收集 / 风控 / 舆情
* 自动化情报提醒

---

## 🧩 功能特性

* ✅ **Bot + User（BotUser）混合架构**

* ✅ 通过 User Account（MTProto）实现真正的群/频道监听

* ✅ Bot 仅用于控制、配置与消息推送，安全隔离

* ✅ Telegram 群组 / 频道监听

* ✅ 多关键词匹配（支持自定义规则）

* ✅ 实时消息推送

* ✅ BotFather 创建与配置

* ✅ 云端运行，长期稳定

* ✅ 可扩展架构，便于二次开发

---

## 🧠 架构设计（BotUser 架构详解）

本项目采用 **Bot + User（BotUser）混合架构**，而非传统“纯 Bot”模式，这是实现 **稳定监听 Telegram 群组 / 频道** 的关键。

### 🔹 为什么必须使用 BotUser 架构？

Telegram 官方 **Bot API 存在天然限制**：

* ❌ Bot **无法主动读取** 未 @ 的群消息
* ❌ Bot **无法加入私有群 / 频道**
* ❌ Bot **无法获取历史消息**

因此，任何“关键词监听 / 群监控”类项目，**仅使用 Bot API 都是不完整的**。

---

### 🔹 本项目的解决方案

本项目采用：

* **User Account（用户号）**

  * 基于 **MTProto** 协议
  * 真实加入群组 / 频道
  * 监听所有实时消息
  * 执行关键词检测逻辑

* **Bot Account（机器人）**

  * 由 **BotFather** 创建
  * 用于指令交互（添加关键词、群组管理等）
  * 将命中结果推送给管理员 / 指定用户

两者 **职责完全分离**，互不越权，长期运行更加稳定。

---

### 🔹 架构示意

```text
Telegram 群组 / 频道
        │
        ▼
┌──────────────────┐
│  User Account     │  ← MTProto 监听全部消息
│  (监听器核心)     │
└──────────────────┘
        │ 关键词匹配
        ▼
┌──────────────────┐
│  规则 / 过滤模块  │
└──────────────────┘
        │ 命中
        ▼
┌──────────────────┐
│  Bot Account      │  ← Bot API 推送通知
│  (控制 & 通知)    │
└──────────────────┘
        │
        ▼
  管理员 / 用户
```

---

### 🔹 BotUser 架构优势总结

* ✅ **100% 可监听群 / 频道消息**
* ✅ 不依赖 @Bot，不会漏消息
* ✅ 可扩展为多 User 并行监听
* ✅ Bot 被封风险极低（仅做通知）
* ✅ 符合实际生产环境使用方式

---

## 📸 项目截图

> 原始截图分辨率较高，已统一缩放展示，点击可查看大图。

### 🔹 核心功能展示

<div align="center">
  <img src="https://github.com/user-attachments/assets/d4147c67-14d0-4da9-b14a-8226ba4b4c67" width="70%" />
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/dad18e15-7855-40b8-951d-b0cfaa3503f3" width="70%" />
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/16ddcf4a-a756-4986-ac57-f32e9afb8c3f" width="70%" />
</div>

---

## 🛠️ 技术关键词

`Telegram` `TG Bot` `关键词监听` `BotFather` `云端机器人` `TG机器人开发`

---

### 🔹 后台 / 运行界面

<details>
<summary>点击展开查看高清截图</summary>

<br />

<div align="center">
  <img src="https://github.com/user-attachments/assets/43dd93eb-29fc-4139-816c-b7f5a9c0c51e" width="85%" />
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/2b3c927e-6e8d-49f7-a159-492e3e5aaeeb" width="85%" />
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/d0a3ec70-6874-4ae7-9526-da72ce4c799b" width="85%" />
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/66ddb255-aaff-45b0-afc6-8c186c5ee838" width="85%" />
</div>
<div align="center">
  <img width="888" height="448" alt="image" src="https://github.com/user-attachments/assets/43dd93eb-29fc-4139-816c-b7f5a9c0c51e" />
  <img width="2878" height="1460" alt="image" src="https://github.com/user-attachments/assets/2b3c927e-6e8d-49f7-a159-492e3e5aaeeb" />
  <img width="2878" height="1450" alt="image" src="https://github.com/user-attachments/assets/d0a3ec70-6874-4ae7-9526-da72ce4c799b" />
  <img width="1012" height="752" alt="image" src="https://github.com/user-attachments/assets/66ddb255-aaff-45b0-afc6-8c186c5ee838" />
</div>

</details>
---

## 📬 联系方式

如你对本项目的 **架构实现、定制开发、商业合作** 感兴趣，欢迎私下交流：

- Telegram：[@Uk233(https://t.me/Uk233) [@CraneVip(https://t.me/Cranevip)
- 双向机器人 [@Sk444bot(https://t.me/Sk444bot)  [@DinBoCsbot(https://t.me/DinBoCsbot)





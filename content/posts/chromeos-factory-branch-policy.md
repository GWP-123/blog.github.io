---
title: "ChromeOS 工厂分支策略：Classic 与 Aluminium 对比"
date: 2026-07-29
draft: false
tags: ["ChromeOS", "Aluminium", "固件"]
---

## Factory Branch Policy 概览

![Factory Branch Policy 对比图](/images/factory-branch-policy.png)

## 核心术语

- **ToT (Tip of Tree)**：代码仓库主干，谷歌持续开发的最新基线。
- **Cherry-pick**：Git 操作，将主干上新的修复 / 功能补丁手动单独合并到老旧分支，分支偏离越大，工作量越高。
- **GSC FW**：Google Security Chip 安全芯片固件，ChromeOS 设备底层安全固件。
- **userdebug image**：厂商产线调试、工厂测试专用镜像，介于开发版与正式发布版之间。
- **Platform-A/B/C**：不同硬件平台（不同一代 CPU / 主板方案）的设备项目代号。

## Aluminium 模式的两大变化

- **代码分支放权**：不再由谷歌统一强制管理平台分支，OEM/ODM 厂商可自主维护镜像，大幅减少跨版本 cherry-pick 合并工作量，解决固件、GSC 芯片版本兼容冲突。
- **配套标准化硬件识别体系**：搭建 Aluminium 识别后台，基于 BOM、AVL 合格物料库生成硬件描述符（Hardware Descriptor），产线校验烧录唯一硬件标识，精准区分各机型硬件配置。

## 两种模式对比

| 维度 | ChromeOS Classic（旧） | Aluminium（新） |
|------|------------------------|-----------------|
| 分支管理权 | Google 统一管控所有平台分支 | 合作伙伴自主管理 |
| 分支约束 | 强制固定版本平台分支 | 无谷歌强制分支规范 |
| 主要弊端 | 分支偏离主干，兼容故障多、大量 cherry-pick 人力消耗 | 厂商自主权衡稳定 / 新功能 / 维护成本，规避旧模式痛点 |
| 适用场景 | 早期 ChromeOS 设备统一管控 | 新一代 Aluminium 架构设备，开放 OEM 自主固件镜像管理 |

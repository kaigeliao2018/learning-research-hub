# Learning Research Hub

> **Deep Learning + Practice Integration for VEX IQ AI Robotics**

这是Kaige为VEX IQ Build Assistant Phase 2建立的学习和研究中心。

不是快速扫过三个项目，而是**学懂 → 实验 → 集成**，最后在主项目中真正应用。

---

## 📚 学习项目

### 1. AutoResearch ⭐⭐⭐ (最高优先级)

**GitHub**: https://github.com/karpathy/autoresearch

**为什么**: VEX IQ Build Assistant的四个并行agents（Analyzer, Packer, Designer, Integrator）需要**自评估 + 自迭代**的能力。AutoResearch正是这个问题的直接解决方案。

**核心概念**: AI agent能够自主修改代码 → 训练验证 → 评估改进 → 保留/回滚，形成一个持续优化的循环。

**在VEX中的应用**:
- Designer Agent: 生成组装步骤 → 迭代优化步骤顺序
- Integrator Agent: QA验证 → 自动改进检查逻辑

**时间投入**: 6.5-9小时
- Phase 1 理论学习: 3-4h
- Phase 2 实验验证: 2-3h
- Phase 3 集成设计: 1.5-2h

---

### 2. nanochat ⭐⭐ (高优先级)

**GitHub**: https://github.com/karpathy/nanochat

**为什么**: 了解极简全栈架构如何被设计。Karpathy在nanochat中删掉了很多"标配功能"，同时保持系统的完整性。这个哲学对VEX Assembly Guide的UI和整体架构有借鉴意义。

**核心概念**: 用最少的代码和依赖，实现完整的训练→推理→WebUI流程。

**在VEX中的应用**:
- UI设计: 极简、直观、高效
- 架构设计: 模块化、可扩展、无冗余

**时间投入**: 4小时
- Phase 1 理论学习: 2h
- Phase 2 实验: 1h
- Phase 3 集成: 1h

---

### 3. graphify ⭐⭐ (中优先级)

**GitHub**: https://github.com/safishamsi/graphify

**为什么**: 快速评估其与VEX部件库可视化、连接约束建模的相关性。

**在VEX中的应用** (待评估):
- 部件库的图结构表示?
- 连接关系的可视化?

**时间投入**: 0.5-4小时（取决于相关性）
- 评估: 1h
- 如果相关: 3-4h
- 如果无关: 0.5h，记录并跳过

---

## 📂 目录结构

```
learning-research-hub/
│
├── README.md (你现在看的)
├── PLAN.md (完整详细学习计划)
├── CLAUDE.md (快速参考)
│
├── projects/
│   ├── autoresearch/          ← Fork下来，仅学习，不修改
│   ├── nanochat/              ← Fork下来，仅学习，不修改
│   └── graphify/              ← Fork下来，快速评估
│
├── research-intake/           ← 你的学习笔记输出
│   ├── autoresearch-overview.md
│   ├── autoresearch-code-walkthrough.md
│   ├── autoresearch-principles.md
│   ├── nanochat-architecture.md
│   └── graphify-relevance-assessment.md
│
├── sandbox/                   ← 实验代码（你的迷你实现）
│   ├── vex-autoresearch-simulation.py
│   ├── vex-ui-mockup.html
│   └── README.md
│
└── integration/               ← 集成方案文档（输出到vex-iq-build-assistant）
    ├── autoresearch-vex-integration-design.md
    ├── nanochat-ui-lessons.md
    └── INTEGRATION-ROADMAP.md
```

---

## 🎯 学习框架

```
Layer 1: 理论学习
  ↓ (阅读代码、理解原理、记笔记)
  ├─ 信息采集
  ├─ 深度代码阅读
  └─ 原理总结
  
Layer 2: 实验验证
  ↓ (动手实现、修改参数、测试想法)
  ├─ 运行官方示例
  └─ 写迷你版本（sandbox/）
  
Layer 3: 项目集成
  → (生成集成方案，最终改造vex-iq-build-assistant)
  ├─ 设计文档
  └─ 任务清单
```

---

## ⏱️ 时间表

| 项目 | Phase 1 | Phase 2 | Phase 3 | 总计 |
|------|---------|---------|---------|------|
| **AutoResearch** | 3-4h | 2-3h | 1.5-2h | 6.5-9h |
| **nanochat** | 2h | 1h | 1h | 4h |
| **graphify** | 1h (评估) | - | - | 0.5-4h |
| **总计** | ~6-7h | ~3-4h | ~2.5-3h | **10-15h** |

---

## ✅ 交付物清单

**学习完成后，这个仓库将包含**:

```
research-intake/
├── autoresearch-overview.md (信息采集)
├── autoresearch-code-walkthrough.md (三圈深度阅读笔记)
├── autoresearch-principles.md (核心5个原则)
├── nanochat-architecture.md (架构学习)
└── graphify-relevance-assessment.md (评估结果)

sandbox/
├── vex-autoresearch-simulation.py (你的迷你实现)
└── vex-ui-mockup.html (UI原型)

integration/
├── autoresearch-vex-integration-design.md (关键输出！)
├── nanochat-ui-lessons.md
└── INTEGRATION-ROADMAP.md (下一步任务)
```

**最重要的是** `integration/` 文件夹中的内容，这些将直接指导如何改造vex-iq-build-assistant。

---

## 🚀 快速开始

### Step 1: Fork三个项目

```bash
# 浏览器操作，或用git：
# https://github.com/karpathy/autoresearch → Fork
# https://github.com/karpathy/nanochat → Fork
# https://github.com/safishamsi/graphify → Fork
```

### Step 2: 克隆到projects/

```bash
cd /Users/kaigeliao/learning-research-hub

git clone https://github.com/kaigeliao2018/autoresearch.git projects/autoresearch
git clone https://github.com/kaigeliao2018/nanochat.git projects/nanochat
git clone https://github.com/kaigeliao2018/graphify.git projects/graphify
```

### Step 3: 提交到GitHub

```bash
git add .
git commit -m "chore: add fork projects and learning structure"
git push origin main
```

### Step 4: 开始学习！

按照PLAN.md的顺序，从AutoResearch Phase 1开始。

---

## 📖 如何使用本仓库

1. **PLAN.md**: 完整的学习路线图。每次学习前，查看对应的Phase描述。
2. **CLAUDE.md**: 快速查阅。导航、时间表、关键决策。
3. **projects/**: 保存三个fork项目，仅供参考，不修改原代码。
4. **research-intake/**: 你的学习笔记。边学边记，用自己的话总结。
5. **sandbox/**: 实验代码。写迷你版本来验证理解。
6. **integration/**: 最终输出。这些文档将指导vex-iq-build-assistant的改造。

---

## 🎯 核心原则

✅ **深度学习**
- 不是快速扫过，而是真正理解
- 用自己的话写笔记，不复制粘贴
- 问"为什么"，不只是"是什么"

✅ **实验验证**
- 在sandbox/中写代码
- 修改参数，测试想法
- 记录发现和启发

✅ **目标导向**
- 始终记住：为了改造vex-iq-build-assistant
- 映射到VEX场景，不是为了学习而学习
- 最终产出是integration/文件夹中的方案

---

## 🔗 相关项目

**主项目**:
- [vex-iq-build-assistant](https://github.com/kaigeliao2018/vex-iq-build-assistant)

**学习项目** (Fork自):
- [AutoResearch](https://github.com/karpathy/autoresearch) by @karpathy
- [nanochat](https://github.com/karpathy/nanochat) by @karpathy
- [graphify](https://github.com/safishamsi/graphify) by @safishamsi

---

## 📝 笔记

- **开始日期**: 2026年4月9日
- **预计完成**: 这周或下周（取决于时间投入）
- **学习者**: Kaige (@kaigeliao2018)
- **机器**: MacBook Pro

---

## 💬 常见问题

**Q: 我没有GPU，能学AutoResearch吗?**
A: 可以。虽然不能跑完整实验，但可以读代码、理解原理、写迷你实现。

**Q: 三个项目都要深学吗?**
A: AutoResearch必须深学（⭐⭐⭐）。nanochat建议深学（⭐⭐）。graphify先快速评估再决定。

**Q: 多久能完成?**
A: 如果每周投入10-15小时，2-3周能完成所有Phase。如果时间少，可以只做AutoResearch的Phase 1-2。

**Q: 学完了怎么办?**
A: 拿integration/文件夹中的方案，改造vex-iq-build-assistant中的Designer和Integrator agents。

---

## 📞 相关联系

维护者: Kaige (@kaigeliao2018)

---

**开始探索吧！🚀**

Remember: **学懂 → 实验 → 集成**

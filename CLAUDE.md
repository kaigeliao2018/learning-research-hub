# learning-research-hub CLAUDE.md

> 快速参考 - 学习体系概览

---

## 📋 核心任务

```
目标: 深度学习三个项目 → 在VEX IQ Build Assistant中实践应用

AutoResearch (⭐⭐⭐ 最高优先级)
  ↓
  自评估 + 自迭代机制
  → Designer Agent + Integrator Agent改造

nanochat (⭐⭐ 高优先级)
  ↓
  极简全栈架构 + UI设计哲学
  → VEX Assembly Guide UI参考

graphify (⭐⭐ 中优先级)
  ↓
  快速评估相关性
  → 可能用于部件库可视化
```

---

## 🗂️ 目录导航

```
learning-research-hub/
│
├── PLAN.md ← 完整详细计划（这周的学习路线图）
├── CLAUDE.md ← 你现在看的（快速参考）
├── README.md ← 项目总描述
│
├── projects/
│   ├── autoresearch/ ← Fork下来的AutoResearch repo
│   ├── nanochat/ ← Fork下来的nanochat repo
│   └── graphify/ ← Fork下来的graphify repo
│
├── research-intake/ ← 你的学习笔记输出
│   ├── autoresearch-overview.md (信息采集总结)
│   ├── autoresearch-code-walkthrough.md (三圈代码阅读笔记)
│   ├── autoresearch-principles.md (核心原则总结)
│   ├── nanochat-architecture.md (架构学习)
│   └── graphify-relevance-assessment.md (相关性评估)
│
├── sandbox/ ← 实验代码（你的迷你实现）
│   ├── vex-autoresearch-simulation.py (VEX场景模拟)
│   └── vex-ui-mockup.html (UI原型)
│
└── integration/ ← 集成方案文档
    ├── autoresearch-vex-integration-design.md (集成设计)
    ├── nanochat-ui-lessons.md (UI设计指引)
    └── INTEGRATION-ROADMAP.md (实施任务表)
```

---

## ⏱️ 时间表

### Phase 1: 理论学习
- **AutoResearch**: 3-4小时
  - 1.1 信息采集 (30min)
  - 1.2 深度代码阅读 - 三圈 (2.5h)
  - 1.3 理论总结 (30min)

- **nanochat**: 2小时
  - 1.1 架构快扫 (30min)
  - 1.2 代码阅读 (1.5h)

- **graphify**: 评估 (1h)

### Phase 2: 实验验证
- **AutoResearch**: 2-3小时
  - 2.1 本地运行 (1-1.5h)
  - 2.2 迷你实现 (1-1.5h)

- **nanochat**: 1小时
  - 2.1 UI参考 + 原型 (1h)

### Phase 3: 集成设计
- **AutoResearch**: 1.5-2小时
  - 3.1 设计文档 (1h)
  - 3.2 任务清单 (0.5-1h)

- **nanochat**: 1小时
  - 3.1 UI设计指引 (1h)

**总计**: 约10-15小时 (这周or下周，你定)

---

## 🎯 关键决策点

确认以下4个问题：

**Q1: 时间承诺**
- [ ] 10-12h这周
- [ ] 5-7h分散
- [ ] 3-4h基础部分

**Q2: GPU资源**
- [ ] 有H100/A100
- [ ] 有Mac GPU (MPS)
- [ ] 没有GPU（只读代码）

**Q3: 学习风格**
- [ ] 逐行读代码，深度优先
- [ ] 先架构，后细节
- [ ] 边学边写代码，实验驱动

**Q4: 改造激进度**
- [ ] 保守：只参考思想
- [ ] 积极：大改造，最大化应用
- [ ] 其他

---

## 📌 本周行动清单

- [ ] Step 1: GitHub仓库创建 ✅
- [ ] Step 2: 本地克隆 + 目录初始化 ✅
- [ ] Step 3: 添加PLAN.md / CLAUDE.md / README.md ⏳
- [ ] Step 4: Fork三个项目到projects/ ⏳
- [ ] Step 5: Git commit + push ⏳
- [ ] Step 6: 开始AutoResearch Phase 1 (理论学习) ⏳

---

## 🔗 三个项目的快速链接

**原始repo**:
- AutoResearch: https://github.com/karpathy/autoresearch
- nanochat: https://github.com/karpathy/nanochat
- graphify: https://github.com/safishamsi/graphify

**你的fork**:
- autoresearch: https://github.com/kaigeliao2018/autoresearch
- nanochat: https://github.com/kaigeliao2018/nanochat
- graphify: https://github.com/kaigeliao2018/graphify

---

## 💡 学习原则

✅ **做**:
- 用自己的话理解和总结
- 在sandbox/中写实验代码
- 记录为什么某个设计的选择
- 映射到VEX场景

❌ **不做**:
- 不是快速扫过一遍
- 不是复制粘贴文档
- 不是单纯读代码，不思考
- 不是无目标的学习

---

## 🚀 现在就开始

1. 下载PLAN.md、CLAUDE.md、README.md
2. 放到 `/Users/kaigeliao/learning-research-hub/`
3. Fork三个项目到projects/
4. `git add . && git commit && git push`
5. 开始学习！

---

记住：**学懂 → 实验 → 集成**

不是快速看过，而是真正掌握！

# Learning Research Hub - 深度学习 + 实践集成计划

> **目标**: 不是快速看过，而是**学懂 → 实验 → 集成**，最后在VEX IQ Build Assistant中真正应用

---

## 📊 学习框架（三层）

```
Layer 1: 理论学习
  ↓ (读代码、理解原理)
  
Layer 2: 实验验证
  ↓ (写实验代码、修改参数、测试)
  
Layer 3: 项目集成
  → 应用到vex-iq-build-assistant (具体代码改动)
```

---

# 项目1：AutoResearch（优先级：最高 ⭐⭐⭐）

## 为什么优先？
你计划的四个并行agents（Analyzer, Packer, Designer, Integrator）需要**自评估 + 自迭代** 的能力。AutoResearch是最直接的参考。

---

## Phase 1: 理论学习（3-4小时）

### 1.1 信息采集 (30min)

```bash
cd learning-research-hub/projects/autoresearch

# 快速导览
cat README.md                 # 理解核心概念
cat train.py | head -100      # 看主训练循环
ls -la runs/                  # 看实验日志格式
```

**产出**: `research-intake/autoresearch-overview.md`
```markdown
## AutoResearch 核心概念

### What it does
- [你的理解，不是copy]

### Key mechanism: Self-evaluation loop
[伪代码或流程图]

### 关键代码片段位置
- Agent修改代码: [文件 + 行号]
- 评估逻辑: [文件 + 行号]
- 迭代决策: [文件 + 行号]
```

### 1.2 深度代码阅读 (2.5小时)

创建学习笔记文件：`research-intake/autoresearch-code-walkthrough.md`

**阅读顺序**（由浅到深）：

```
第1圈 (40min) - 流程理解
├─ agent.py (或类似)
│  └─ class Agent: 
│     ├─ modify_code()     # 修改代码逻辑
│     ├─ train()           # 运行一轮训练
│     └─ evaluate()        # 评估结果
└─ main.py
   └─ loop: modify → train → eval → keep/discard

第2圈 (60min) - 关键细节
├─ 怎样"修改"代码? (随机? 启发式?)
├─ 怎样"评估"改进? (什么指标?)
├─ 怎样"决策"保留/丢弃? (阈值? 历史?)
└─ 如何处理失败案例? (异常恢复)

第3圈 (50min) - 与你的场景的映射
├─ 对比: AutoResearch的"train"功能
│        vs VEX Designer生成组装步骤
├─ 对比: AutoResearch的"evaluate"功能
│        vs VEX Integrator检查步骤有效性
└─ 差异分析: 我需要改什么才能用?
```

**每一圈产出一个文档**：
```markdown
## AutoResearch Code Deep Dive - 第1圈：流程

### Agent execution loop
```python
# 伪代码（你的理解）
while not converged:
    # 1. 基于历史，生成代码修改提案
    modification = agent.propose_modification(history)
    
    # 2. 应用修改
    apply_change(modification)
    
    # 3. 训练并测试
    result = train_and_test(duration=5min)
    
    # 4. 评估是否改进
    improved = result.score > best_score
    
    # 5. 保留或回滚
    if improved:
        keep_change(modification)
        best_score = result.score
    else:
        revert_change(modification)
```

### 关键问题与答案
Q: Agent怎么知道该改什么？
A: [你读代码后的答案，不是AI生成]

Q: 评估指标是什么？
A: [...]
```

### 1.3 理论总结 (30min)

**产出**: `research-intake/autoresearch-principles.md`

```markdown
## AutoResearch 的5个核心原则

### 原则1: 原子性改动
- 每次修改一个可独立评估的单元
- 应用场景: VEX中，每个改动应该是？

### 原则2: 快速反馈循环
- 训练5分钟 → 即刻反馈
- 应用场景: VEX中，组装步骤生成的快速验证

### 原则3: 历史感知
- Agent记住之前的尝试，避免重复
- 应用场景: VEX中，Designer应该记住什么？

### 原则4: 保守决策
- 只有明确改进才保留
- 应用场景: VEX组装指南生成时的风险管理

### 原则5: 可解释性
- 能说出为什么保留/丢弃
- 应用场景: VEX生成的指南为什么这样？
```

---

## Phase 2: 实验验证（2-3小时）

### 2.1 本地运行AutoResearch（官方案例）

创建文件：`projects/autoresearch/MY-EXPERIMENTS.md`

```bash
cd projects/autoresearch

# 按官方文档跑一遍（可能需要GPU，如果没有则跳过运行，只看代码）
# bash runs/simple_experiment.sh

# 如果你没有GPU，至少要：
# 1. 理解输出日志格式
cat runs/sample_run/log.json
# 2. 看最终生成的report
cat runs/sample_run/report.md
```

**产出**: `projects/autoresearch/MY-EXPERIMENTS.md`

```markdown
## Experiment 1: 理解Agent的修改策略

### 实验问题
AutoResearch的Agent用什么策略决定"改什么"?

### 我的假设
[你的假设]

### 验证方法
1. 在train.py中添加日志，打印每次modification
2. 运行5轮迭代
3. 分析日志，看修改的模式

### 发现
[结果]

### 对VEX的启发
- Designer可以用类似的XX策略生成步骤
- Integrator可以借鉴YY评估方式
```

### 2.2 迷你实现：VEX场景的AutoResearch模拟

**在你的learning-research-hub里创建沙箱**：

```
learning-research-hub/
└── sandbox/
    ├── vex-autoresearch-simulation.py  (迷你版本)
    └── README.md
```

**vex-autoresearch-simulation.py** 的目标：

```python
"""
模拟: AutoResearch原理应用到VEX组装指南生成

场景: Designer Agent生成组装步骤
问题: 如何让Designer不断优化生成的步骤顺序?

简化版本:
1. 初始步骤顺序 (随机或启发式)
2. 对每个候选顺序评估: 是否逻辑连贯? 是否可实现?
3. 保留改进的顺序，回滚失败的
4. 迭代
"""

class VexAssemblyDesigner:
    def __init__(self):
        self.best_steps = self.generate_initial_steps()
        self.best_score = self.evaluate(self.best_steps)
        self.history = []
    
    def propose_modification(self):
        """建议改动：重新排序某两个步骤"""
        pass
    
    def evaluate(self, steps):
        """评估一个步骤序列的质量"""
        # 指标: 逻辑连贯度、可实现性等
        pass
    
    def iterate(self, num_rounds=10):
        """主循环"""
        for round in range(num_rounds):
            # 1. 提议改动
            # 2. 评估
            # 3. 决策保留/回滚
            pass

# 你的实验
if __name__ == "__main__":
    designer = VexAssemblyDesigner()
    designer.iterate(num_rounds=10)
    print("最终步骤:", designer.best_steps)
```

**产出**: 
- 代码正常运行
- 输出日志显示迭代过程
- 文档说明为什么这个模拟有用

---

## Phase 3: 项目集成（1.5-2小时）

### 3.1 生成集成设计文档

**产出**: `integration/autoresearch-vex-integration-design.md`

```markdown
## AutoResearch → VEX IQ Build Assistant 集成方案

### 目标
让四个并行agents（特别是Designer + Integrator）具备自评估能力

### 具体改动点

#### 改动1: Designer Agent 自迭代
位置: vex-iq-build-assistant/agents/designer.py

当前逻辑:
```python
def generate_steps(model):
    # 一次性生成，然后返回
    return steps
```

改进逻辑 (基于AutoResearch):
```python
def generate_steps_with_iteration(model, num_iterations=5):
    best_steps = initial_generation()
    best_score = evaluate_steps(best_steps)
    
    for _ in range(num_iterations):
        # 提议改动: 重新排序某些步骤
        candidate = propose_reordering(best_steps)
        
        # 评估候选
        score = evaluate_steps(candidate)
        
        # 保留或回滚
        if score > best_score:
            best_steps = candidate
            best_score = score
    
    return best_steps
```

#### 改动2: Integrator Agent QA循环
位置: vex-iq-build-assistant/agents/integrator.py

基于AutoResearch的eval机制:
- [具体改动描述]
- [伪代码]

### 实施优先级
1. **Phase 2.1** (立即): Designer自迭代 (最有影响)
2. **Phase 2.2**: Integrator评估循环
3. **Phase 2.3**: Analyzer和Packer的微调

### 风险评估
- 迭代太多会很慢 → 需要设置合理的iteration count
- 评估函数定义困难 → 从启发式开始，逐步优化

### 成功指标
- [ ] Designer生成的步骤质量改进10%+
- [ ] 重复运行时结果稳定性提高
- [ ] Integrator能明确说出为什么某个步骤可行/不可行
```

### 3.2 创建集成任务列表

**产出**: `integration/INTEGRATION-ROADMAP.md`

```markdown
## VEX IQ Build Assistant - Phase 2 集成路线图

### Task 1: Designer Agent 自评估迭代
- [ ] 复制AutoResearch的self-eval loop结构
- [ ] 定义"步骤序列质量评分函数"
- [ ] 实现重新排序的modification
- [ ] 集成到Designer类
- [ ] 测试: 生成10个组装指南，对比迭代前后质量

**预计工作量**: 8-10小时
**开始时间**: [你的日期]
**负责人**: Kaige

### Task 2: Integrator Agent 评估循环
...

### Task 3: 监控和调优
- [ ] 记录每次迭代的性能
- [ ] 找到最优的iteration count
- [ ] 编写性能报告
```

---

# 项目2：nanochat（优先级：高 ⭐⭐）

## 为什么这个项目？
VEX IQ Build Assistant的最终UI可能要参考nanochat的极简设计哲学。而且了解极简全栈架构有助于优化你的pipeline。

---

## Phase 1: 理论学习（2小时）

### 1.1 架构快扫 (30min)

```markdown
# nanochat 架构概览

## 整体流程（你用自己的话描述）
输入 → 数据准备 → 训练 → 推理 → WebUI

## 为什么"极简"?
- [Karpathy删掉了什么常见功能]
- [为什么可以删]

## 关键设计决策
1. [第一个关键决策 + 为什么]
2. [第二个关键决策 + 为什么]
3. ...
```

### 1.2 深度代码阅读 (1.5小时)

**按模块学习**:

```
① Tokenization (tokenizer.rs)
   └─ 问题: VEX中有类似的"离散化"需求吗?
   
② Data preparation (data.py)
   └─ 问题: VEX部件库如何组织数据以供agents学习?
   
③ Training loop (train.py)
   └─ 问题: 什么是最小化的训练loop?
   
④ Inference (inference.py)
   └─ 问题: 如何快速生成输出?
   
⑤ Web UI (web/)
   └─ 问题: VEX Assembly Guide UI应该有什么功能?
```

---

## Phase 2: 实验验证（1小时）

### 2.1 UI参考

即使你不能跑完整的nanochat训练（需要GPU），也可以：

```bash
cd projects/nanochat

# 查看web UI代码
cat web/index.html
cat web/app.py  # (如果有)

# 问: VEX Assembly Guide的WebUI需要什么?
# - 实时交互?
# - 步骤可视化?
# - 用户反馈?
```

**产出**: `sandbox/vex-ui-mockup.html` 

参考nanochat的设计，创建VEX Assembly Guide UI的原型

---

## Phase 3: 项目集成（1小时）

**产出**: `integration/nanochat-ui-lessons.md`

```markdown
## nanochat → VEX UI 设计指引

### 学到的极简原则
1. [原则1] - VEX中的应用
2. [原则2] - VEX中的应用

### VEX Assembly Guide UI的设计决策
- 单页还是多页?
- 实时生成还是批量?
- 用户可交互吗?
- 如何展示3D模型?

### 可复用的代码片段
- [来自nanochat的某个组件]
- [你改造后用于VEX的版本]
```

---

# 项目3：graphify（优先级：中 ⭐⭐）

## 评估：值不值得深学？

**快速问卷** (1小时决定)

```bash
cd projects/graphify

# 1. 这是什么?
cat README.md

# 2. 与VEX的关联是什么?
# 问: VEX部件库可以表示为图吗?
# - 节点: 部件
# - 边: 连接关系
# - 可视化库存吗?

# 3. 复杂度?
find . -name "*.py" | wc -l
```

**决策标准**:
- [ ] 如果与VEX高度相关 → 深学（3-4小时）
- [ ] 如果关联中等 → 浅学（1小时）
- [ ] 如果无关 → 记录但暂不优先

**产出**: `research-intake/graphify-relevance-assessment.md`

```markdown
## graphify 相关性评估

### VEX中的图结构应用场景
- 部件库的可视化?
- 连接约束的表示?
- 步骤依赖的建模?

### graphify 能否帮助?
[是/否 + 理由]

### 决策
☐ 深学 (投入3-4h)
☐ 浅学 (参考工具)
☐ 跳过 (目前无关)
```

---

# 📅 时间投资与收益表

## AutoResearch
| 阶段 | 投入 | 收益 |
|------|------|------|
| Phase 1 理论 | 3-4h | 理解自迭代原理 |
| Phase 2 实验 | 2-3h | 手写迷你版本，验证理解 |
| Phase 3 集成 | 1.5-2h | Designer/Integrator改造方案 |
| **小计** | **6.5-9h** | **→ 直接应用到VEX** |

## nanochat
| 阶段 | 投入 | 收益 |
|------|------|------|
| Phase 1 理论 | 2h | 极简架构哲学 |
| Phase 2 实验 | 1h | UI原型 |
| Phase 3 集成 | 1h | VEX UI设计决策 |
| **小计** | **4h** | **→ VEX UI改造参考** |

## graphify
| 决策 | 投入 | 收益 |
|------|------|------|
| 如果相关 | 3-4h | 部件库可视化 |
| 如果无关 | 0.5h | 记录评估结果 |

---

## 📝 总体交付物清单

**学习完成后，你将有**:

```
learning-research-hub/
├── README.md (总导航，更新)
├── PLAN.md (这个计划)
├── CLAUDE.md (快速参考)
│
├── projects/
│   ├── autoresearch/
│   │   └── MY-EXPERIMENTS.md         ← 你的实验日志
│   ├── nanochat/
│   │   └── (代码无修改，只学习)
│   └── graphify/
│
├── research-intake/
│   ├── autoresearch-overview.md
│   ├── autoresearch-code-walkthrough.md (三圈详细笔记)
│   ├── autoresearch-principles.md
│   ├── nanochat-architecture.md
│   └── graphify-relevance-assessment.md
│
├── sandbox/
│   ├── vex-autoresearch-simulation.py  ← 你的迷你实现
│   └── vex-ui-mockup.html              ← 你的UI原型
│
└── integration/
    ├── autoresearch-vex-integration-design.md  ← 关键输出
    ├── nanochat-ui-lessons.md
    └── INTEGRATION-ROADMAP.md                  ← 下一步任务
```

**和，你的主项目中**:

```
vex-iq-build-assistant/
├── docs/
│   ├── RESEARCH.md (新增，汇总学习)
│   └── (其他保持不变)
├── agents/
│   └── designer.py (改进版本，集成自迭代)
└── (最终代码改动)
```

---

## 🎯 核心问题确认

**开始前，确认这些**:

1. **时间承诺**: 你有10-12小时这周来做这个学习吗? 还是分散在几周?

2. **GPU可用性**: 
   - [ ] 有H100/A100可跑AutoResearch实验
   - [ ] 有Mac GPU (MPS) 可跑轻量版本
   - [ ] 没有GPU，只能读代码 + 伪代码模拟

3. **学习风格偏好**:
   - [ ] 我喜欢逐行读代码，深度优先
   - [ ] 我喜欢先整体架构，再深入细节
   - [ ] 我喜欢边学边写代码，实验驱动

4. **集成目标**:
   - [ ] 只是"参考思想"，不要太激进改动
   - [ ] 积极改造，最大化应用AutoResearch原理
   - [ ] 其他

---

## ✅ 下一步

你确认这个计划后，我们按顺序：

1. **这周** (Week 1): 
   - 建立learning-research-hub仓库 ✅
   - Fork三个项目 ⏳
   - 完成AutoResearch Phase 1 (理论学习) ⏳

2. **下周** (Week 2):
   - AutoResearch Phase 2-3 (实验 + 集成设计) ⏳
   - nanochat Phase 1-2 ⏳
   - 开始vex-iq-build-assistant的代码修改 ⏳

---

**记住**: 这不是快速扫过，而是**学懂 → 实验 → 集成**！

开始探索吧！🚀

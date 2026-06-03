# learn-while-vibe

**AI 辅助学习技能包** — 让 Claude Code、codex或者其它什么支持skill的东西成为你的学习教练。

三个技能构成完整的学习闭环：**做完复盘 → 严厉批评 → 方法讲透**。

---

## 包含的技能

### 1. review-after-work

**工作复盘报告**

完成一个项目后，生成结构化的 `.md` 复盘报告，包含：

| 章节 | 内容 |
|---|---|
| 核心目的 | 你真正想做什么，实际做到了什么 |
| **技术路线** | 用连贯叙述文字讲清楚方法选择和逻辑链（即后文的/make-it-clear） |
| 工作流 | 实际的工作节点和工具调用链 |
| 核心难题 | 遇到了什么卡点，怎么解决的 |
| 新技能 | 沉淀了哪些可复用的方法 |
| 改进点 | 用户侧和 AI 侧各有什么问题 |
| 总体评价 | 冷静的一段话总结 |

**触发方式**：说 `/review-after-work`、"工作复盘"、"复盘报告"、"写一份复盘"

---

### 2. criticise-me

**严厉批评模式**

严格审查你在当前对话中的：prompt 质量、问题描述、debug 方法、设计思维、验收标准、任务节奏、偷懒思维。

我希望这些话你听进去了但别往心里去，所以这个skill不会自动生成文件供你保存——实际上，“保存了=看过”也是严重的拖延症问题，因此你现在、立刻、马上就要做好被批评的准备！

输出结构：

| 章节 | 内容 |
|---|---|
| 最严重的问题 | 直指根本原因，附具体证据 |
| 逐项审查 | prompt / 需求 / debug / 文件 / 设计 / 推进节奏 |
| 最该醒悟的一件事 | 一段话，打到要害 |
| 最低限度改进建议 | 3-5 条，下次就能用 |
| 下次提问模板 | 可直接复用的问题框架 |

**触发方式**：说 `/criticise-me`、"批评我"、"挑毛病"、"骂我"、"给我挑刺"

---

### 3. make-it-clear

**技术路线讲透**

用一段流畅、逻辑承接紧密的叙述文字，把项目的路线规划和每一步的方法选择讲清楚。

不同于表格和列表，这个技能输出的是**连贯的文章**：

- 每个步骤自然包含：目的 → 输入 → 方法 → 为什么选它 → 输出
- 步骤之间有逻辑承接：上一步的结果如何暴露下一步的必要性
- 用具体数字而非抽象描述
- 方法选择有对比：为什么不用替代方案

**触发方式**：说 `/make-it-clear`、"讲清楚路线"、"把方法逻辑串起来"、"理清技术路线"

(我真的很讨厌一大堆名词然而我完全看不懂它们之间有什么联系的无力感)
---

## 安装方式

### 方法一：克隆到 skills 目录

```bash
cd ~/.claude/skills
git clone https://github.com/Zhaimiaoyizhi/learn-while-vibe.git
```

然后将各技能目录复制到 skills 根目录：

```bash
cp -r learn-while-vibe/review-after-work .
cp -r learn-while-vibe/criticize-me .
cp -r learn-while-vibe/criticise-me .
cp -r learn-while-vibe/make-it-clear .
```

### 方法二：符号链接

```bash
cd ~/.claude/skills
git clone https://github.com/Zhaimiaoyizhi/learn-while-vibe.git
ln -s learn-while-vibe/review-after-work .
ln -s learn-while-vibe/criticize-me .
ln -s learn-while-vibe/criticise-me .
ln -s learn-while-vibe/make-it-clear .
```
当然————叫你的agent安装是最省事的！
---

## 使用场景

```
完成一个数据分析项目
  → /review-after-work    生成复盘报告 + 技术路线叙述
  → /criticise-me         检视自己的学习方法和提问质量
  → /make-it-clear        用流畅文字把方法论讲透
```

适用但不限于：
- 生物信息分析作业（正是我说使用的，好吧，其实DDL只有几小时的时候我不会管那么多的）
- 编程项目开发
- 数据科学实验
- 任何需要"做完之后搞明白为什么这样做"的场景（那也就是说是所有场景！所以你需要给我的项目点star！）

---

## 设计理念

> 学习不是"AI 帮我做完了"，而是"我能讲清楚为什么这样做"。

这三个技能分别对应学习闭环的三个环节：

1. **review-after-work**：记录做了什么（客观复盘）
2. **criticise-me**：审视做得怎样（严厉自检）
3. **make-it-clear**：检验是否真懂（方法论阐述）

如果你发现自己只能完成第 1 步而跳过第 2、3 步，说明你可能在"旁观 AI 工作"而非"自己在学习"。

---
当然，随着我持续的学习与使用，这个技能库会不断更新~
## License

MIT

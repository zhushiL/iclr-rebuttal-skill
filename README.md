# iclr-rebuttal

面向 ICLR 等机器学习会议作者的 Codex skill。给它审稿意见、论文相关段落和手头已有的证据，它可以帮你判断**评审究竟在质疑哪个科学结论**，再起草逐点回复、讨论期跟进或给领域主席（AC）的总结。默认用中文分析、英文起草，也可以指定语言和篇幅。

例如，审稿人写道 *“Can you evaluate on more tasks?”* 如果下文提到设计选择和测试共用一批任务，重点就在于验证是否独立。此时，在一个未参与设计选择的任务上复验原结论，可能比在原任务上增加几十个样本更有说服力。如果评语只提到任务数量，skill 会保留其他合理解释，并指出哪些原文线索有助于判断。

## 安装

在 Codex 中输入下面这句话。

```text
使用 $skill-installer 安装 https://github.com/zhushiL/iclr-rebuttal-skill/tree/main/iclr-rebuttal
```

也可以在终端手动安装。

```bash
git clone https://github.com/zhushiL/iclr-rebuttal-skill.git
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R iclr-rebuttal-skill/iclr-rebuttal "${CODEX_HOME:-$HOME/.codex}/skills/"
```

安装后重新打开 Codex，用 `$iclr-rebuttal` 调用。这份 skill 由 Markdown 和 YAML 组成，无需安装额外的 Python 或 Node.js 包。

## 使用示例

**读懂一条评语。** 只贴原文也能开始。若有论文段落或评审后续追问，一并提供会更容易判断。

```text
使用 $iclr-rebuttal 分析这条评语，先不用写英文回复。
“The auxiliary metric improves, but does that help the downstream task
under the same compute budget?”
请区分他明确要求的比较、你推测的科学顾虑，以及现有证据还缺什么。
```

**起草逐点 rebuttal。** 可以把实际文件名、评审问题编号、实验完成状态和篇幅写进请求。

```text
使用 $iclr-rebuttal，根据 review.md、论文第 4 节和 results.csv，
给 Reviewer 2 的 W1 和 Q3 写英文回复，合计 250 词以内。
其中独立测试集已经跑完，三随机种子复验还在进行。请按实际状态措辞。
```

**处理讨论期最后一条消息。** 同一讨论串里的提醒、致谢和 AC 总结可以分别起草。

```text
使用 $iclr-rebuttal。审稿人回复 “I will reconsider my assessment.”
帮我拟一个标题和两句英文致谢，不重列实验，也不用再请他重新评估。
```

## 13 篇公开案例怎么用

案例来自 ICLR 2025 和 ICLR 2026。按**当前评语涉及的科学问题**检索，每篇都能追到具体讨论。领域、年份、论文可见均分和单个评审的改分情况作为标签。改分幅度按当届评分档位计算。[打开完整案例库](iclr-rebuttal/references/case-library.md)

| 当前评语的科学问题 | 可以借鉴的案例与做法 |
|---|---|
| 调参和验证是否独立？展示的样例是否有代表性？ | Diffusion Planner 在新任务上复验设计结论。FASA 根据追问补充跨模型的分布。 |
| 提升来自哪个组件或训练条件？ | MemoryVLA 检查动作分块这一替代解释。VLM4VLA 将分辨率和图像来源拆开比较。 |
| 差异很小，如何区分统计波动和实际价值？ | Imputation 分设定检验效应并报告例外。The Polar Express 对照数值精度与下游损失。 |
| 评审要的是补引用、界定贡献，还是补性能对照？ | Embodied-R1 区分引用与技术增量。BiasFreeBench 按评估对象和输出类型与近邻比较。 |

每个案例区分评审明说的要求、根据上下文推断的顾虑、作者提供的证据，以及评审后来确认的范围。这样既能借鉴成功回应，也能看清哪些问题在改分或录用后依然存在。

## 常用入口

- [技能主文件](iclr-rebuttal/SKILL.md)说明如何读评语、核对证据和组织回复。
- [英文回复模板](iclr-rebuttal/references/templates.md)涵盖逐点回应、理论澄清、追问和 AC 总结。
- [讨论期跟进与致谢](iclr-rebuttal/references/follow-up.md)按最新一条评语选择合适的回复。
- [通用科学问题手册](iclr-rebuttal/references/general-playbook.md)和[具身智能问题手册](iclr-rebuttal/references/embodied-playbook.md)给出证明、统计、基线公平性及部署问题的证据选择方法。

## 许可证

本仓库的原创内容采用 [MIT 许可证](LICENSE)。案例中链接的论文、评审和会议资料按原来源的许可使用。

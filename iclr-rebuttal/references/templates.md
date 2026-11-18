# 原创回复模板

以下英文是编辑归纳，**不是案例论文的原文摘录**。尖括号表示需据材料替换的变量；证据不足时在工作稿中保留明确的中文待提供项。按实际平台限制分帖，不默认固定字数。

## 1. 总体回应

```markdown
Dear Reviewers and Area Chair,

Thank you for the constructive feedback. Our responses focus on <issue A> and <issue B>, with the following completed additions:

- **<Main concern>:** <proof, experiment, or protocol correction and bounded finding>. See <section/table>.
- **<Main concern>:** <clarification or controlled comparison>. See <section/table>.
- **Scope and presentation:** We revised <specific claim/term> to <accurate wording> and clarified <remaining limitation>.

The point-by-point responses below explain the evidence and changes for each reviewer.
```

若部分实验未完成，删去相应 completed 条目，不用共同开头把全部计划包装成成果。

## 2. 实验类逐点回复

```markdown
### W1 & Q2 — <specific concern>

<Direct answer in one sentence.>

To test <the reviewer's hypothesis>, we evaluated <setting>, holding <controls> fixed. <One-sentence result.>

| Method / condition | <metric and unit> | <uncertainty, if available> |
|---|---:|---:|
| <matched baseline> | <verified result> | <verified uncertainty> |
| <proposed method> | <verified result> | <verified uncertainty> |

These results support <bounded claim> under <tested conditions>.

We have added <specific change> to <version, section, table/figure>.
```

对已核实的一个事实，用结论+位置两句即可。边界优先融入条件与结论，必要时才另写一句说明尚未验证的内容。不要为了模板制造实验或局限。

理论与协议问题使用第 9、10 节，不机械套用结果表。

## 3. 澄清训练与推理

```markdown
### Q3 — Use of privileged information

The privileged state is used only to construct training targets; it is not an input during evaluation. At test time, the policy receives <actual inputs> and produces <actual outputs>.

We have clarified the training and inference paths in <location>. The results in <table> were obtained using <evaluation inputs/protocol>.
```

只有核实过接口与代码/协议才这样写。若评估实际上使用 oracle，就如实说明，并缩小部署结论。

## 4. 术语修正与范围收缩

```markdown
We agree that <original term> can imply <unsupported property>. Our method requires <actual training or system dependency>. We have replaced it with <precise term> in <locations>.

The demonstrated contribution is <supported claim>. <Broader capability> remains untested and is now stated as a limitation.
```

## 5. 公平比较与尚未完成的实验

```markdown
The existing comparison measures <deployment/system-level question>; it does not isolate <architectural or training effect>. The methods differ in <data/checkpoint/inputs/budget>.

We therefore report <matched comparison, if completed> separately from <contextual comparison>. We have revised <claim/table label> to make this distinction explicit.
```

未完成时可用：

```markdown
We agree that <requested control> would be needed to establish <strong claim>. We have not completed that evaluation. The current evidence supports only <narrower claim>, and we have revised the manuscript accordingly.
```

不要用“其他论文也这样做”代替公平性论证，也不要写“预计提升 X%”。

## 6. 追问回应

```markdown
Thank you for clarifying the question. Our earlier response addressed <previous interpretation>, whereas your question concerns <actual issue>.

<Direct answer and new evidence.>

We have updated <location>. <Any unresolved part> remains open because <specific reason>.
```

承认理解偏差后直接纠正，不反复道歉。评审认可后的回复可缩为一句致谢加一句已落实修订。

## 7. 给 AC 的状态总结

```markdown
Dear Area Chair,

We summarize the evidence added during the discussion and the remaining limitations.

| Concern | Completed response / evidence | Revision | Discussion status |
|---|---|---|---|
| <R-ID: issue> | <bounded result> | <location> | <reviewer explicitly acknowledged / follow-up pending / no reply observed> |

The principal remaining limitation is <limitation>. We have restricted <claim> accordingly.

For the discussion record, <reviewer ID> explicitly stated <accurate paraphrase with comment link>. We have not received a follow-up from <ID>; we therefore do not interpret that thread as resolved.
```

仅在确有必要时列评分，而且分别标注本人明示、作者转述、AC 推测。摘要以证据为主，不写催分或请求录用的话术。

## 8. 文字压缩顺序

先删重复致谢和重复贡献描述，再把整段问题缩成准确主题，合并同一 reviewer 的重复疑问，保留直接答案、关键数字、控制条件与修改位置。最后才把方法细节移到论文。不能为了省字删掉决定公平性或结论范围的条件。

## 9. 理论澄清与真实修正

```markdown
### Q<number> — <definition, assumption, or proof gap>

<Direct statement of whether the concern identifies an ambiguity or an error.>

Under <explicit assumptions>, <lemma/construction> establishes <intermediate result>, which implies <bounded conclusion>. The missing step is <short, checkable argument>.

We have <corrected the statement / added the construction> in <revised location, with old-to-new numbering if needed>. This change affects <scope>; <remaining claim> follows from <verified dependency>.
```

若确有错误，用 `The stated expression was incorrect; it should be …`；若只是对象不同，定义两个对象。不得在未检查依赖链时断言“不影响任何结论”。

## 10. 评分协议与偏差方向

```markdown
Each example allows <number> attempts. We declare success when <condition>, stop when <condition>, and aggregate scores using <rule>. Missing evaluations are <representation and handling>.

We agree that <specific feature> may favor <condition>. This factor therefore does not explain <observed direction> under <stated assumptions>. It does not rule out <other unresolved confound>.

We have corrected <figure/description> and clarified these rules in <location>.
```

只有论证了偏差方向才能这样写；无法判定时应提出控制分析，不套用“对我们不利所以更可信”。

## 11. 部分同意与替代证据

```markdown
We agree that <verified criticism>. This limits <claim A>; the evidence in <location> still supports <narrower claim B> under <conditions>. We have revised the wording accordingly.
```

如果没有完成原请求：

```markdown
We have not completed <requested test>. The additional <related analysis> examines <specific subquestion>, but does not directly establish <original target>. We therefore retain <remaining issue> as an open limitation.
```

已有结果与 reviewer 请求接近，不代表二者等价；写清交集与缺口。

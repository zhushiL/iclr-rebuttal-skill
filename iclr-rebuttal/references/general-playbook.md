# 通用 Rebuttal：按争议选择回答与证据

本页按争议整理可用的证据和写法，英文句式为原创模板，仅在事实核实时使用。需要真实对照时，从[统一案例库](case-library.md)按本稿的具体问题选例。

三个样本分别涉及理论、LLM 评测和数值优化。它们说明：回复结构可以共用，但证明、协议核对、控制实验与限制声明不能彼此替代。

## 1. 先判断争议属于哪一层

| 争议层次 | 要回答的问题 | 合适的回应动作 |
|---|---|---|
| 事实或定义 | reviewer 对方法、符号、设置的理解是否准确？ | 明确对象、范围、单位或协议，给原位置与修订位置 |
| 真实错误 | 原稿的公式、表述或实现是否有误？ | 承认并更正，说明影响范围，检查依赖结论 |
| 证据充分性 | 当前证据能否区分两种解释？ | 补证明、反例、控制实验或统计分析 |
| 结论强度 | 结果是否被推广到未验证范围？ | 明确成立条件，收缩过强措辞 |
| 价值判断 | 共识事实是否仍被赋予不同意义？ | 承认共识，清晰说明不同推论及依据 |

**同意事实不等于同意推论。** 可以承认没有实现某基线、某模型不符合趋势、某措辞不准，同时解释这些事实具体削弱哪项结论、尚未推翻哪项结论。不要把局部让步写成全面退让，也不要把核心结果成立当作拒绝修正的理由。

> We agree that <verified fact>. This limits <claim A>, while the evidence in <location> still supports <claim B> under <conditions>.

## 2. 表达歧义与真实错误分开处理

若概念本身正确但读者容易误解，先直接区分对象，再改正文。若原文确有错误，明确更正，不能只写“we clarify”。

《Transformers are Inherently Succinct》的作者先区分 tiling instance 与 UHAT 输入长度，并接受部分模型条件和措辞限制；另一条回复明确修正指数表述，补引理和证明定位。[概念与范围回应](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=W3lI2c87Ib)；[错误修正与引理](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=sehzYk9odU)。

决策：

- 若只是两个长度变量混用，定义每个量以及它们的关系，不重复整篇证明。
- 若公式应为另一数量级，检查后续引理、定理和摘要是否依赖该公式。
- 若核心论证不受影响，给出依赖链或具体证明位置，而非仅声明“不影响结论”。

> These two quantities refer to different objects: <definition A> and <definition B>. We have made this distinction explicit in <location>.

> The stated expression was incorrect; it should be <correct expression>. This changes <affected statement>. The argument for <remaining claim> uses <verified condition>.

## 3. 理论问题：给可检查的论证，而非性能表

对“假设不明、构造不完整、推导跳步”的回应，先列出评审质疑的命题与所需条件，再给最短可核验的论证：定义 → 引理/构造 → 推论。完整证明可以放修订稿，回复需说明新增步骤怎样解决缺口。

在上述理论论文中，作者补技术条件与完整构造；rC5n 随后明确认可并维持 8 分。这支持“使证明可核查”的案例观察，不支持“补引理一定升分”的因果主张。[技术补充](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=UVX7N5l6FJ)；[reviewer 反馈](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=MdssjsGQ4X)。

需要逐一核对：定理量词、渐近变量、假设、计算模型、精度要求，以及结论是存在性还是普遍性。“可以构造”不能写成“所有模型都如此”。

> Under assumptions <A>, Lemma <L> establishes <intermediate result>, which yields <claim>. We have added the missing construction in <location>.

若补充证明仍依赖额外假设，应同步修改定理陈述，不能只把条件藏在 rebuttal 中。

## 4. 评测协议：解释指标究竟奖励什么

对“评测是否不公平”的质疑，先把判分过程写到足够精确：每例有几次机会、何时算成功、如何聚合、失败与缺失怎样编码。然后判断协议偏差的方向，而非只说“沿用标准设置”。

《LLMs Get Lost In Multi-Turn Conversation》解释 N 个 shards 对应 N 次作答机会，任一次正确即算成功，并承认图示不够清楚；作者指出这类机会设置有利于多轮。C44a 随后认可结论仍成立。[协议回应](https://openreview.net/forum?id=VKGTGGcwl6&noteId=pjsk4N7ZSm)；[后续反馈](https://openreview.net/forum?id=VKGTGGcwl6&noteId=TERrUjfOH4)。

这类回答应保留两个层次：协议事实是否明确，以及在该协议下结论的含义。偏差有利于某方法，可以削弱特定批评，却不能自动消除其他混杂因素。

> Each example provides <number> prediction opportunities, and success is defined as <rule>. This favors <condition> with respect to <specific factor>; it does not control for <remaining factor>.

## 5. 例外与缺失值：直接报告，不修饰成一致趋势

当 reviewer 找到反例时，区分“主趋势有例外”“测量不适用”“结果未知”。不要把未评测值当零分，也不要把部分模型的现象推广到所有模型。

上述多轮论文承认部分模型没有 lost-in-the-middle 现象，解释上下文范围，并说明 Phi4/OLMo2 的 summarization 缺失项以 dash 表示。其 recap 实验支持部分恢复，而不是全面解决问题。[例外与缺失值回应](https://openreview.net/forum?id=VKGTGGcwl6&noteId=WOCDInrElP)。

可用动作：改正文量词，给出例外列表，修正表注，限定机制解释。若数据只支持多个可能解释，就把解释写成假说。

> The trend is not uniform across all models. We observe <exception> and have revised the claim to apply to <supported subset>.

> The dash denotes an unavailable evaluation, not zero performance. We have clarified this in the table caption.

## 6. 成本与效果：先对齐比较轴

“相同迭代数”“相同 FLOPs”“相同运行时间”“达到相同损失所需时间”回答不同问题。对速度或效率质疑，先说明论文到底比较哪一轴，再报告另一轴是否测量。

《Polar Express》澄清同迭代成本不等于更快，强调相同 runtime 下的 loss，并定位 Appendix H。这个做法可迁移到优化器、推理加速、压缩和系统论文。[成本比较回应](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=li4JTxp19l)。

> Our claim concerns <quality> at matched <runtime/budget>, rather than lower cost per iteration. The relevant comparison is reported in <location>.

不要只凭一项子程序耗时证明端到端加速；条件不匹配时报告差异，不强行给单一“效率倍数”。

## 7. 数值精度是否转化为下游收益？

当质疑涉及近似误差或迭代次数时，分别测量中间量和最终任务指标。更精确的数值解不一定改善训练结果，较小的误差也不自动等于更好的泛化。

《Polar Express》补 SVD 参照和 2–30 次迭代对照，报告约 5–6 次后下游 loss 未继续改善；对 10B tokens 时效果差距缩小也如实说明。[迭代与下游结果](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=WxGdtjjFqO)；[更长训练结果](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=ctE4LXkQPr)。

> Increasing <precision/iterations> improves <intermediate metric>, but we do not observe a corresponding gain in <downstream metric> beyond <tested range>.

由此提出实用参数选择时，应明确来自哪些规模和任务，不将观察拐点写成普遍最优值。

## 8. 没有完成的请求：保留可见缺口

可以说明未实现某方法、实验仍运行、请求超出验证范围。回答需明确“未完成什么”和“现有证据支持什么”，不造结果，不把替代分析写成原实验已完成。

《Polar Express》承认 Zolo-PD 未实现；视觉实验先写计划，后续才报告完成。checkpoint KL 的请求则被小奇异值子空间消融与假说替代，因此不能记成已直接回答 KL 问题。[未实现基线](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=AlKq4OT8T1)；[替代分析](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=CCrXcYzSMX)。

> We have not completed <requested test>. We instead provide <related analysis>, which informs <narrow issue> but does not directly establish <original target>.

跨轮次用版本和日期更新完成状态；新增实验即使差异很小也应报告。不要只保留有利规模或任务。

## 9. 范围限制不必都转化为补实验

如果请求是扩展到创造性任务、真实用户或全新应用域，先判断它是否直接动摇当前主张。当前主张已受限定时，简洁承认限制可以足够；主张覆盖了该范围时，就需补证据或收缩结论。

多轮论文对创造性任务与真实用户局限作简短承认，展示了不把每条建议扩展为新研究项目的做法。是否充分，仍取决于原论文的实际主张。

> Our evaluation covers <tested setting>. We have not established the result for <new setting>, and we now state this limitation explicitly.

## 10. 一条回复只保留一条可核验主线

推荐顺序是：直接判断 → 最小充分依据 → 对结论的影响 → 具体修订。短问题可以两句解决；复杂问题用小标题拆分。无需每条都写长致谢、贡献总结和未来工作。

- 理论稿用条件、证明和反例；评测稿用协议、偏差方向和分项结果；优化稿用成本轴、近似误差及下游效果。
- 引用已有实验时指出它究竟排除了什么，不把“相关证据”写成“已证明”。
- 评审认可、作者自评、AC 推测分别记录；没有可见后答时保留“未确认”。
- 在交付前检查所有表述中的 all、always、necessary、fully resolved 是否有足够依据。

上述做法的共同目标是让 reviewer 能快速检查答案，而不是制造一套与论文内容无关的固定话术。

## 11. 新颖性：给机制和操作定义，不靠术语增重

针对“只是已有组件的组合”，先说清哪些组件沿用已有工作，再用可检查的规则、目标或接口说明新增关系。解释它改变了什么训练行为或信息条件，以及什么对照可以区分该设计与已有原则。性能优势能支持其效用，不能单独证明文献意义上的首创。

对 reasoning、adaptation、coordination 等容易产生歧义的术语，优先给操作定义：实际输入、计算过程、监督信号、输出及对应的可观察能力。用户希望保留术语时，评估能否由这些事实支持清晰定义，不默认必须删词。某个模块允许信息进入，不等于模型已经依赖该信息；训练目标也不等于已实现所有语义上可能暗示的能力。

操作定义在引言或首次使用处建立一次。方法章节用实现落实定义，实验用相应行为检验，结论回收同一范围，不在每节加入互相偏移的新解释。

## 12. 按比较对分离模块、训练策略和数据的影响

先列清哪几行构成实际比较，再核对数据来源与量、初始化、模块、训练策略、更新数、有效 batch、损失及后训练设置中与问题有关的项。无需把每项都塞入回复，但不能把未核实项概括成“所有其他条件完全一致”。同一确认不能从一对实验扩展到整张表。

例如，完整模型同时采用模块 M 和训练策略 R，而控制行没有 R，二者差值无法单独归因于 M。若已有不使用 R 的 M 变体，先在无 R 的共同条件下比较模块，再在 M 固定时比较 R。这支持各自条件下的增益，不自动证明两因素的全局加性或协同效应。

条件不明确时先核实，不能把未知写成已知不公平；确认存在混杂时才把结果限定为配置级比较。以下边界尤其容易混淆：

- 同数据量不保证同数据、同训练策略或同初始化。
- 同更新次数和 batch 不保证相同 FLOPs、GPU 小时或实际运行时间。
- 在同骨干上实现某方法的设计原则，不等于完整复现该方法，命名和结论应明确适配范围。
- 去掉额外预训练语料而保留基础模型权重，不是从零训练。若同时改变训练阶段或策略，其差值也不是纯数据贡献。
- 有无额外预训练的两个配置可以检验对额外语料的依赖，但不是数据规模曲线。判断新设计的效果优先用针对该因素的匹配对照，不要求跨系统结果承担全部归因。

联合结构和各因素的边际频率也要分开。若策略改变路径共现关系，可用匹配边际概率的控制检验联合设计是否仍有收益。该结果支持所比较的联合策略，不能自动将全部差值归因于唯一某个状态或机制。

## 13. 多种子、不确定性与数值计算

先确定估计目标和独立重复单位，再选择区间方法。记录重跑的是预训练、后训练还是仅评估，以及哪些 checkpoint 固定。只重跑后训练时，报告的是给定预训练初始化下的下游变异，不是整个训练流程的变异。

若每次独立训练得到一个任务平均指标，应先按论文定义计算每次运行的指标，再跨运行算均值和样本 SD。不要把不同任务的离散程度当作 seed SD，也不要把同一策略的大量帧、相关 episode 或 checkpoint 当成额外独立训练重复。

在独立运行、所选模型和分布假设适用时，可对运行级均值使用双侧 Student-t 区间：

\[
\bar{x} \pm t_{1-\alpha/2,n-1}\,s/\sqrt{n}.
\]

这里的 n 是独立运行数，不是总帧数或总试验次数。小 n 的区间需说明其参数化性质和条件，不能把精确的小数位当成很强的可靠性证据。置信水平和方法按任务、数据结构与用户要求选择，不固定要求三 seed 或 95% 区间。

- **二项试验区间回答不同问题**：对固定策略的成功次数可在相应独立性假设下估计成功概率区间，但这不能代替跨训练运行的不确定性。
- **均值区间不是差值区间**：不要仅凭各方法 CI 重叠与否宣布显著或不显著；相同 seed 编号本身不建立有效配对。没有合适配对设计或差值分析时，只报告观察差值和各自不确定性。
- **描述统计不是因果归因**：按帧汇总的门值或注意力箱线图可以描述分布，不能当成同样数量的独立样本，也不能由分组相关性证明机制。

用原始计数或未舍入运行指标计算 SD 和 CI。按任务等权的宏平均与按试验数加权的总体成功率在分母不等时不同，先核对聚合规则。一般从未舍入结果计算差值后统一展示；若用户或论文已明确采用显示均值相减，则保持该约定并注明，不能混用两种口径。百分比率之差用百分点，相对增幅使用明确的分母。

计算后检查合计、任务分母、均值、样本 SD、CI、差值和粗体最优标记。发现原始记录与表格冲突时确认权威版本后再传播修正，不为凑齐旧总数修改原始数据。

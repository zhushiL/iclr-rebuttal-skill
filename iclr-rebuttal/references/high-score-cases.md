# 三篇跨领域高分论文：通用 rebuttal 技巧

本页保存三篇论文的逐评审记录及可见评分，读取于 2026-11-15。按科学问题选例见[统一案例库](case-library.md)。

## 选取标准与分数口径

本次采用透明的工作标准：**当前可见 Official Review 评分均值至少 7，且至少三位 reviewer 给 8 分或以上，并有实质作者回复**。这是选样标准，不是 ICLR 官方“高分”分档，也不代表全会排名。先从官方奖项名单发现候选，再逐篇读原论坛核实评分，未以获奖或 Oral 直接代替分数。

| 论文 | 领域 | 可见 reviewer 评分 | 算术均值 | 结果及额外认可 |
|---|---|---|---:|---|
| [Transformers are Inherently Succinct](https://openreview.net/forum?id=Yxz92UuPLQ) | Transformer 表达能力、复杂性理论 | aJWw: 4；cqAR: 8；rC5n: 8；TYFS: 8 | 7.0 | Oral；Outstanding Paper |
| [LLMs Get Lost In Multi-Turn Conversation](https://openreview.net/forum?id=VKGTGGcwl6) | LLM 多轮评测、可靠性 | RY95: 8；yCDA: 8；ig5S: 10；C44a: 6 | 8.0 | Oral；Outstanding Paper |
| [The Polar Express: Optimal Matrix Sign Methods and their Application to the Muon Algorithm](https://openreview.net/forum?id=yRtgZ1K8hO) | 优化、数值线性代数 | caWQ: 8；Xn5s: 8；kcTx: 10；WacA: 6 | 8.0 | Oral；Honorable Mention |

奖项据 [ICLR 官方公告](https://blog.iclr.cc/2026/04/23/announcing-the-iclr-2026-outstanding-papers/)。评分据各论坛的四条 Official Review，**不是最终讨论后评分**。ICLR 2026 发生评审回退，详见 [流程说明](process.md)。第一篇存在显著分歧，应称“多数高分但有技术争议”，不能写成四位一致高度认可。

这是获奖候选中的目的性样本，适合提炼跨领域写法，不能证明回复格式带来高分或奖项。以下实验和修改状态均按作者评论记录；未独立重做证明、复现实验或逐处核验历史 PDF。

<a id="succinct"></a>

## A. Transformers are Inherently Succinct

### 主要争议与过程

reviewer aJWw 认可研究方向，但对规模参数、编码方式和关键证明链条提出疑问，给 4 分并表示若澄清则可能提高。其他三位给 8 分，仍要求明确实际架构适用性、构造细节和可学习性边界。

11-19 作者逐 reviewer 回应，对最复杂的评审分成两帖；采用短引述 `Comment/Question` 后接 `Answer`。11-28 rC5n 明确表示问题已解决并维持评分。11-29 作者总结如实说初始 8、8、8、4 尚未改变，aJWw 的后续答复不可见。

### 观察到的有效做法

1. **先找定义层面的分歧。** [首帖](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=W3lI2c87Ib) 区分“tiling problem instance 的参数”与“固定模型接受的配置字符串长度”，说明 unary 编码和固定参数。回应不是笼统要求 reviewer 重读证明，而是把误解发生的位置具体写出来。
2. **把澄清和真实修正同时报告。** [续帖](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=sehzYk9odU) 一方面解释 reviewer 对 unary/binary 的理解差异，另一方面承认文中某处应写为 `2^poly(n)`，并补 Lemmas 8、9，使原先埋在证明中的构造成为可直接引用的陈述。
3. **用适当的限定语保护正确结论。** 作者将普遍式表述改为“can be”，对 RNN 比较增加 [UHAT 可表达语言范围](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=7tndWNdgvW)；[对 TYFS](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=x5L1mRPQjE) 明确区分最坏情形难度、易处理子类，以及表示存在性和能否学到该表示。
4. **修订位置含旧新编号映射。** [对 rC5n](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=UVX7N5l6FJ) 指出原 Proposition 对应修订后的 Lemma，并给附录构造。理论稿不能只说“added details”，需要指出证明依赖如何闭合。

### 反馈与边界

[rC5n](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=MdssjsGQ4X) 明确认可并维持 8。[作者总结](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=h8To6nlRrx) 未声称 aJWw 已提高评分。[meta-review](https://openreview.net/forum?id=Yxz92UuPLQ&noteId=xSblRDUAVL) 的 4→8 是推测，不能写成实际提分。

**可迁移结论：** 对“证明可能不对”的回应，按定义、假设、构造、界限、推论逐层检查；该纠正的地方明确纠正，核心结果是否保留另行论证。不要用“只是误解”掩盖原文确实需要修正的内容。

<a id="multi-turn"></a>

## B. LLMs Get Lost In Multi-Turn Conversation

### 主要争议与过程

四位 reviewer 的评分为 8、8、10、6，问题集中在评分协议、shard 自然性、上下文长度、纠错反馈，以及合成对话对真实用户的代表性。作者于 11-21 用每位 reviewer 一帖、Q/W 编号逐项回答，长短随问题而变。

### 观察到的有效做法

1. **把评估协议讲成可执行流程。** [对 C44a](https://openreview.net/forum?id=VKGTGGcwl6&noteId=pjsk4N7ZSm) 说明 N 个 shards 允许最多 N 次作答，任一答案正确就成功并提前结束；同时承认 Figure 10 没展示每轮评分，承诺修图。
2. **分析偏差的方向，而非否认所有偏差。** 同帖承认提前猜对、基准记忆或判分不严格可能给多轮条件优势。作者据此论证：这些因素不能解释多轮更差的方向。[C44a 后续](https://openreview.net/forum?id=VKGTGGcwl6&noteId=TERrUjfOH4) 明确认可这一点并维持正面评价。这不能推出所有混杂都消除了，尤其不能替代真实用户验证。
3. **直接说哪些模型不符合某个子结论。** [对 ig5S](https://openreview.net/forum?id=VKGTGGcwl6&noteId=WOCDInrElP) 承认 Claude 3.7 Sonnet 和 Gemini 2.5 Pro 未呈现明显 loss-in-the-middle，避免将平均现象写成每个模型都成立。
4. **给异常处理规则和失败定义。** 同帖说明上下文需求与不适用的 model/task 组合，Phi-4、OLMo2 的 summarization 为未运行的横杠，不是零分；对数学例子承认错误在于未合并子答案，而非算术能力缺失。
5. **复用已有最相关证据，保留未覆盖问题。** 作者用 recap 实验回应部分纠错问题，报告它能部分改善但未达到单轮表现；[对 RY95](https://openreview.net/forum?id=VKGTGGcwl6&noteId=5lLPsdoHne) 仍承认更自然的中途纠错未被充分覆盖。[对 yCDA](https://openreview.net/forum?id=VKGTGGcwl6&noteId=to1SK4UsOq) 简短接受真实用户与开放任务的限制，没有强行补一个无关实验。

### 反馈与边界

[ig5S](https://openreview.net/forum?id=VKGTGGcwl6&noteId=xYDqOvenpv) 表示看过回复且无进一步具体疑问；C44a 明确维持正评。其余两位无可见后续确认。[meta-review](https://openreview.net/forum?id=VKGTGGcwl6&noteId=FNFcbn3Yfz) 仍将真实用户研究不足列为未解决部分。

**可迁移结论：** 对 benchmark 质疑，优先明确输入、作答机会、停止条件、评分聚合和缺失值规则；再逐个分析可能偏差能否改变结论。承认某个子发现只适用于部分模型，通常比维护泛化措辞更严谨。

<a id="polar-express"></a>

## C. The Polar Express

### 主要争议与过程

四位 reviewer 为 8、8、10、6。关注同迭代数是否等于同运行成本、精确 SVD 的对照、近似指标与下游效果的关系，以及更长训练和视觉任务的泛化。

11-21 发布逐点评审回复及版本变更说明，明确有些实验仍在准备；12-04 作者再报告视觉任务完成，给具体附录位置。这个时间线反映“计划→完成”两个状态，不将后来的完成状态倒写到首轮回复中。

### 观察到的有效做法

1. **先纠正比较口径。** [对 caWQ](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=li4JTxp19l) 说明相关多项式迭代采用相同类型运算、每次成本相当，主张是相同 runtime 下更低 loss，而不是凭迭代数就声称运行更快。
2. **补能决定结论的对照。** [对 WacA](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=WxGdtjjFqO) 加精确 SVD 与 2–30 次迭代对照，报告在其设置中 5–6 次之后下游 loss 不再改善。这样能解释为何继续提高数值精度未必有实际收益。
3. **用最小例子解释技术问题。** [对 Xn5s 的续帖](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=jTeKUX4vnu) 用固定点与小矩阵说明不收敛现象，并承认那些基线本来就为快速粗近似设计，避免把任务目标不同描述成对手失效。
4. **如实报告收益缩小和效果较弱的设置。** [10B-token 结果](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=ctE4LXkQPr) 说明优势仍在但差距缩小；[视觉实验总结](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=LvrFqHdqfV) 明说不同 Muon 变体差异较小，其额外收益仍需研究。
5. **承诺落实有独立回执。** [11-21 版本说明](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=nhaTapFtkH) 将已完成结果与视觉实验计划分列；[后续回复](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=Ah2VX0rvY1) 明确指出已加入 Appendix H.3。
6. **未做的对照明确说未做。** [对 kcTx](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=AlKq4OT8T1) 承认未实现 Zolo-PD。可以解释技术预期，但不能将其写为测量结果。

### 反馈与边界

WacA 的 [追问](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=sTWmnaaF0L) 要求比较 checkpoint 输出 KL；作者的 [后答](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=CCrXcYzSMX) 改做小奇异值子空间干预，作为解释同 loss 现象的假说证据。它并不等于完成了 KL 请求，也不证明模型输出相同。[AC](https://openreview.net/forum?id=yRtgZ1K8hO&noteId=e8hsal3ipQ) 推测 WacA 可能升到 8；无 reviewer 本人明确改分记录。

**可迁移结论：** 面对性能质疑，明确目标指标和资源约束，补精确或理想对照以揭示实际瓶颈；展示不利或较弱结果并据此调整结论。替代实验需要说明它回答了原问题的哪一部分。

## 跨领域结论

| 技巧 | 新样本支持 | 实际写作动作 |
|---|---|---|
| 同意事实，单独判断推论 | 理论稿承认表述/构造需修正；对话稿承认评分偏差 | 分开写原稿错在哪里、这是否改变核心结论 |
| 问题类型决定证据类型 | 理论补引理；benchmark 补协议；优化补对照 | 不把每个问题都转换成“补更多实验” |
| 诚实限定适用范围 | 理论最坏情形/可学习性；对话部分模型；优化视觉收益小 | 写明能证明什么、不能证明什么 |
| 降低核查成本 | 编号、短问答、章节/图表、旧新定理映射 | 直接回答后给具体位置与变更内容 |
| 最小充分回应 | 对话稿接受开放任务限制仅短答；理论问题详答 | 篇幅按争议复杂度分配，致谢不替代答案 |
| 区分计划、完成和认可 | Polar Express 分阶段更新；理论稿不伪称升分 | 每条证据与讨论状态单独维护 |

完整通用操作建议见 [通用问题手册](general-playbook.md)。

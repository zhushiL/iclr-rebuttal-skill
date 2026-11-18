# ICLR 2026 普通案例 · 同一评审上调一档（4 → 6）

两例均核对同一位评审的总体 Rating。4 和 6 是该届量表中略低于、略高于接收门槛的相邻档位。ICLR 2026 后来回滚评分，这里记录讨论期修订时的变化。跨年比较按各届量表计算档位。[流程说明](process.md) · [按科学问题查全部案例](case-library.md)

<a id="fasa"></a>

## FASA: Frequency-Aware Sparse Attention · VxaW

**评分依据。** 原评为 4，评审本人签署的讨论期修改中 Rating 为 6。其余分项另列。[原评](https://openreview.net/forum?id=FnSgecCEwg&noteId=iiZkbExMZg) · [修订记录](https://openreview.net/revisions?id=iiZkbExMZg)

**争议与回应。** 评审担心几张热图有选择性，难以说明频率块的稀疏性，还质疑选择频率块是否依赖任务与校准数据。作者补充定量证据并澄清设置。跟进中，评审保留了对理论贡献的意见，也指出仅靠汇总表仍难判断分布形状，建议画累计分布。作者随后在附录 A.6 图 12 给出六个模型的分布。这是上调评分与保留实质意见同时存在的案例。后补的图应按实际次序记为答复追问，不能倒推为此前改分的原因。[完整讨论](https://cseweb.ucsd.edu/~jmcauley/reviews/iclr26b.pdf) · [第二轮作者答复](https://openreview.net/forum?id=FnSgecCEwg&noteId=ka1Sig1kzO)

**可迁移做法。** 遇到“例子可能是挑出来的”，先明确总体、测量单位及抽样方式，再展示覆盖该总体的分布和例外。理论依据与观测到的经验规律分开回答，结论限定在实际测试过的设置。

<a id="biasfreebench"></a>

## BiasFreeBench · 156a

**评分依据。** 原评 Rating 为 4。156a 在评论中表示会提高评分，未写目标数值；同一评审的讨论期修订字段为 6。作者归档中的原评、答复和跟进位于第 4–6 页。[原评](https://openreview.net/forum?id=Ncf2LFDT4e&noteId=BqI2gxcTho) · [修订记录](https://openreview.net/revisions?id=BqI2gxcTho) · [讨论归档](https://cseweb.ucsd.edu/~jmcauley/reviews/iclr26a.pdf#page=4)

**争议与回应。** 156a 追问与 FLEX 等评测的区别、如何理解对去偏方法的评价，以及单一指标的覆盖范围。作者用对照表说明相关工作覆盖哪类方法、是否评价生成文本，并分别解释有标准答案与开放生成时如何计分。评审随后明确点名，贡献与新颖性的澄清回应了其顾虑。[作者比较表](https://openreview.net/forum?id=Ncf2LFDT4e&noteId=Vcyu8Fjkqi)

**可迁移做法。** 遇到“有什么新意”，以评审点名的近邻为起点，选取能改变结论的比较维度，例如被评估的对象、所需标签、允许的输出类型。用一个具体输入说明评分规则，再界定指标能支持的主张。该案例没有证明一个标量可覆盖所有公平性维度。

**提醒措辞的对照。** 156a 表示上调，而收到几乎相同提醒的 zx3y 明确维持原分，认为这些解释应在初稿出现；归档中未见 hVui 在提醒后回复。向 AC 汇报时，只记录各人实际表态。无需从同一句提醒推算改分概率。[156a 的回复](https://cseweb.ucsd.edu/~jmcauley/reviews/iclr26a.pdf#page=6) · [zx3y 的回复](https://cseweb.ucsd.edu/~jmcauley/reviews/iclr26a.pdf#page=10) · [hVui 的讨论串](https://cseweb.ucsd.edu/~jmcauley/reviews/iclr26a.pdf#page=17)

## 在新稿上怎么用

先从评语中写出一句会影响推荐的判断，再选能让评审检验这句话的证据。FASA 的问题涉及现象是否普遍，适合给分布；BiasFreeBench 的问题涉及工作与近邻有何区别，适合给协议对照。给 AC 的总结分别写出已有证据、评审认可的范围和仍保留的意见。只在同一 reviewer 的原始和更新评分都可追溯时写出精确分差。

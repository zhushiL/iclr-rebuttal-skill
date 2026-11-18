# 六篇 ICLR 2026 具身投稿：回复格式与讨论过程

本页保存逐篇讨论记录。可从[统一案例库](case-library.md)按机制归因、比较公平性、创新归属或部署成本等问题定位本页和其他论文。

阅读日期：2026-11-15。下列“观察”来自公开论坛；“提炼”是编辑建议。实验和修订均按作者评论记录，不代表独立复现。链接带 `noteId` 可定位具体评论。日期采用论坛显示的日历日期，不据此推算投稿截止时区。

## 样本范围

| 来源 | 论文 | 具身主题 | 可见回复数（含评审、决定等） | 最终决定 |
|---|---|---|---:|---|
| 用户提供 | [HAMLET](https://openreview.net/forum?id=KcJ9U0x6kO) | VLA 历史记忆 | 23 | Accept (Poster) |
| 用户提供 | [MemoryVLA](https://openreview.net/forum?id=54U3XHf7qq) | 感知/认知记忆 | 20 | Accept (Poster) |
| 用户提供 | [VLM4VLA](https://openreview.net/forum?id=tc2UsBeODW) | VLM 到机器人控制的迁移 | 21 | Accept (Poster) |
| 补充检索 | [Embodied-R1](https://openreview.net/forum?id=i5wlozMFsQ) | 指点表示、具身推理和机器人执行 | 30，含一条删除记录 | Accept (Poster) |
| 补充检索 | [ERA](https://openreview.net/forum?id=hqFNqVQEUd) | 具身规划、操作及在线 RL | 19 | Reject |
| 补充检索 | [MemER / Scaling up Memory for Robotic Control via Experience Retrieval](https://openreview.net/forum?id=1dH4ARGdwD) | 多分钟记忆与分层控制 | 21 | Accept (Poster) |

补充论文覆盖“表示/推理”“训练与规划”“记忆与部署”。保留拒稿对照，避免把录用论文的每个写法都包装成成功技巧。ENACT 检索候选因论坛属于 workshop 被排除。

<a id="hamlet"></a>

## 1. HAMLET：编号对齐与修改落实

**观察到的过程。** 11-19 作者按 W/Q 回答，长回复分开发布；11-21 至 11-28 有 reviewer 反馈和后续实验；11-25 的总体回应后续更新，汇总新增表格及措辞修订。

- [yS5A 首轮回复](https://openreview.net/forum?id=KcJ9U0x6kO&noteId=ltLzqh1wZp) 用 `[W1]`、`[W2]` 短标题，分别补较长时域任务和 TCL 消融；不是仅声称“原稿已有充分实验”。
- [续帖](https://openreview.net/forum?id=KcJ9U0x6kO&noteId=2SdpMyjqvt) 区分基线问题与术语问题。[reviewer 追问](https://openreview.net/forum?id=KcJ9U0x6kO&noteId=UhmUt0b1PD) 认可主要回应但仍要求修改 plug-and-play，并明确表示提高到 6；[作者跟进](https://openreview.net/forum?id=KcJ9U0x6kO&noteId=IQOZxHO8b2) 报告已替换措辞。
- [oHKU 的首轮回复](https://openreview.net/forum?id=KcJ9U0x6kO&noteId=xQuCLWnVAF) 将 W2 拆成架构覆盖和修改成本两项。[后续回复](https://openreview.net/forum?id=KcJ9U0x6kO&noteId=LGet9ZOnj4) 澄清 Pi0-FAST 的具体模型并提供新表及 Appendix B.1 定位。
- [General Response](https://openreview.net/forum?id=KcJ9U0x6kO&noteId=sH9UaswjSQ) 把修改分列到表和章节，并说明颜色标记。

**提炼。** 保留 reviewer 编号；一个问题有两个可检验部分时拆分。接受准确术语，随后报告修改完成。第一轮解决不了的内容，在追问中补增量，不重复整篇方法。

**限制与反例。** 对 JGoo，[首次解释](https://openreview.net/forum?id=KcJ9U0x6kO&noteId=1jqltb9BUz) 用失败恢复解释普通 benchmark 收益；[reviewer 指出](https://openreview.net/forum?id=KcJ9U0x6kO&noteId=fjTsJ7AFRl) 训练轨迹多为成功示范，要求解释 OOD 恢复来源。作者再答后未见该 reviewer 明确关闭问题。合理机制叙述不等于因果验证。

<a id="memoryvla"></a>

## 2. MemoryVLA：合并重复问题、共享证据、精确定位

**观察到的过程。** 11-25 集中发布各 reviewer 逐点回复和全局修订说明；11-26 出现认可和追问；12-04 再给 AC 写证据总结。

- [F2kP 回复](https://openreview.net/forum?id=54U3XHf7qq&noteId=7qrlNtHR52) 合并 `W1 & Q2`，先用轨迹长度表解释不同 memory length，再补消融，避免把相同问题回答两遍。
- PZt6 回复分 [1/3](https://openreview.net/forum?id=54U3XHf7qq&noteId=ftrBlpTnpL)、[2/3](https://openreview.net/forum?id=54U3XHf7qq&noteId=nRGLKKfDS8)、[3/3](https://openreview.net/forum?id=54U3XHf7qq&noteId=VWNqbUU59H)：新增 Mikasa-Robo，报告协议；对 action chunking 的替代解释补 chunk 消融；再单独说明真机训练条件匹配。
- [MmT3 的效率回复](https://openreview.net/forum?id=54U3XHf7qq&noteId=bVKdEiUmo2) 把硬件、精度、运行次数和延迟/显存表放在回答附近；[reviewer](https://openreview.net/forum?id=54U3XHf7qq&noteId=UgFj0Vsc0k) 明确支持录用。
- [全局回应](https://openreview.net/forum?id=54U3XHf7qq&noteId=j14X8dV3JB) 按 J.1–J.10 索引新增材料；[AC 总结](https://openreview.net/forum?id=54U3XHf7qq&noteId=387aIQOpSU) 再按 reviewer 重排，便于不同读者导航。

**提炼。** 同一证据可复用，但每条回复需要直接回答对应疑问。共享表的协议与版本必须一致。AC 总结应是证据目录而非礼貌话堆叠。

**限制与反例。** [meta-review](https://openreview.net/forum?id=54U3XHf7qq&noteId=AOd5I4trAT) 的部分升分是 AC 推测。相机视角泛化仍列为限制。注意作者多处把绝对成功率差写成 `%`；新稿宜明确用百分点。不要把作者对 chunking 或视角原因的绝对表述照抄成普遍规律。

<a id="vlm4vla"></a>

## 3. VLM4VLA：把替代解释变成实验，承认理解偏差

**观察到的过程。** 11-23 发分帖回应；11-26 reviewer 追问；11-28 再答并报告修订；12-01 给重新分配的 AC 总结。

- [n8E9 Part1](https://openreview.net/forum?id=tc2UsBeODW&noteId=8QhT0JqjV1) 将“视觉编码器微调收益是否来自分辨率或仿真外观”拆为两个假设，分别给分辨率×冻结设置和真实图像控制监督实验。
- [C7oU 首轮](https://openreview.net/forum?id=tc2UsBeODW&noteId=uQD4udnsxg) 回答超参数公平性，说明选择协议并补学习率扫描；[reviewer 追问](https://openreview.net/forum?id=tc2UsBeODW&noteId=8qZcWqqDYh) 要求进一步说明相关性和实际指导意义。
- [第二轮](https://openreview.net/forum?id=tc2UsBeODW&noteId=dbqgu7I8Jp) 明确承认之前误解“其他 VL 任务”，随后给 grounding 相关性分析；未隔离的其他能力留作未解决项。
- [ZXC9 回应](https://openreview.net/forum?id=tc2UsBeODW&noteId=rAupgRwzWH) 接受限制仿真实验结论；[修订说明](https://openreview.net/forum?id=tc2UsBeODW&noteId=Fw8GJHY36h) 列具体章节。

**提炼。** 用实验检验 reviewer 的解释；坦承未知机理；追问时先校正问题理解。公平性要写清模型、训练与选择协议，不能只写“相同超参数所以公平”。

**限制与反例。** [AC 总结](https://openreview.net/forum?id=tc2UsBeODW&noteId=rilK4GkPVn) 明确有两位未回复。第二轮 grounding 的 r 与 R² 数值在常规单自变量带截距回归解释下并不对应，不能直接复制为统计范例；需回查拟合定义和原始数据。由少量模型观察到的相关性不能证明普遍必要条件。

<a id="embodied-r1"></a>

## 4. Embodied-R1：术语与新颖性争议要拆开

**观察到的过程。** 11-26 多组分帖；11-27 至 11-28 与 LhSQ 继续争论分类、引用及创新来源；作者最终报告术语、相关工作与贡献表述修订。

- [gZir 1/3](https://openreview.net/forum?id=i5wlozMFsQ&noteId=dKSOTVJCXz) 按问题给新 LIBERO 结果，同时区分高层轨迹和低层力控职责。
- [gZir 2/3](https://openreview.net/forum?id=i5wlozMFsQ&noteId=rgrO9fUWz4) 对 OpenVLA 数值差异说明原来源、复现和 OpenVLA-OFT 版本，展示追溯基线的必要性。
- [分类跟进](https://openreview.net/forum?id=i5wlozMFsQ&noteId=AiKjnLbBFZ) 接受严格 VLA 定义，提出替换术语；[最终修订说明](https://openreview.net/forum?id=i5wlozMFsQ&noteId=tYB9KEdf3q) 报告已改表格类别、相关工作和贡献措辞。
- [关于引用的追问](https://openreview.net/forum?id=i5wlozMFsQ&noteId=eFultssw3P) 明确 reviewer 原意是补引用，不是要求新性能比较；[作者后答](https://openreview.net/forum?id=i5wlozMFsQ&noteId=DUYBavraaD) 承认共用架构和算法，将贡献定位于能力定义、数据与奖励设计。

**提炼。** 将“标签不准”“缺引用”“技术增量不足”分开解决。给共享代码框架以准确归属，但别用“应用领域不同”自动免除引用义务。

**限制与反例。** [LhSQ 最后意见](https://openreview.net/forum?id=i5wlozMFsQ&noteId=bceA7RNAXm) 仍认为创新不足，只表示会适当升分。录用不意味着该分歧消失。长篇强调“本质不同”没有自动说服对方。基线表也需重新核算：该帖 pi0-fast 四项算术平均与所列 Avg 不一致，不能照搬数字。新增 RGB-D 架构同时改变训练方案，不能只把收益归于结构。

<a id="era"></a>

## 5. ERA：拒稿对照，区分接口澄清与核心有效性

**观察到的过程。** 11-21 总体回应，11-22 对四位 reviewer 分帖逐点回复；可见串没有后续 reviewer 评论。最终 Reject。

- [总体回应](https://openreview.net/forum?id=hqFNqVQEUd&noteId=3vkHGW5HYP) 先说明研究问题是多轮具身交互，并列新增真机材料。
- [KpUu 回复](https://openreview.net/forum?id=hqFNqVQEUd&noteId=7Xh6ABwtqM) 按观察—行动—环境更新循环澄清不是单步 QA；[oracle 澄清](https://openreview.net/forum?id=hqFNqVQEUd&noteId=TPoKmRisGa) 区分训练标签和推理输入。
- [真机及比较回应](https://openreview.net/forum?id=hqFNqVQEUd&noteId=9ieK8Giq7c) 补真实机器人结果，但对同数据微调大模型比较主要给范围解释。
- [成本回应](https://openreview.net/forum?id=hqFNqVQEUd&noteId=h1Ke7zy6d3) 把一次性训练/数据成本和部署摊销分开讨论。

**提炼。** 清晰描绘训练与推理接口，能有效回答“用了 oracle 吗”。成本问题要拆开生成、训练、单次推理和部署量；最好给可复算假设而非只有“小模型更便宜”。

**限制与反例。** [meta-review](https://openreview.net/forum?id=hqFNqVQEUd&noteId=52jMbCqgDp) 认可若干澄清，但仍记录新颖性、比较等争议。补真机不能替代同条件对照。不同回复对“恢复能力在 EPL 或 RL 何时出现”的措辞有张力，应做跨回复一致性检查。meta-review 的评审质量疑虑不是对任何个人违规的独立证实，不应作为 rebuttal 话术。

<a id="memer"></a>

## 6. MemER：部署约束、标注成本与现实边界

**观察到的过程。** 11-19 首轮回复，之后更新实验与稿件；11-21、11-25、11-28 收到反馈；总体回应 12-01 更新讨论状态。

- [eE1T 1/2](https://openreview.net/forum?id=1dH4ARGdwD&noteId=BwQQzc1TSS) 开头先给主要变更目录，再逐项回应；标注成本拆成子任务生成、结束标记与关键帧规则，并说明按任务设规则而非逐帧人工标注。
- [eE1T 2/2](https://openreview.net/forum?id=1dH4ARGdwD&noteId=bKjPZH45Rf) 分开高低层延迟、显存与频率，解释为什么使用两个模型；[reviewer](https://openreview.net/forum?id=1dH4ARGdwD&noteId=iMSUsR6Tmq) 认可新增分析及限制说明，明确表示从 4 改到 6。
- [uYHS 2/2](https://openreview.net/forum?id=1dH4ARGdwD&noteId=OhUTEbjd82) 用物体原位置何时从滑动窗口消失的任务实例解释长程记忆，并承认小时级任务仍需删除机制。
- [缺失参考文献的回复](https://openreview.net/forum?id=1dH4ARGdwD&noteId=3YfAXpMXYl) 请求明确 [1,2,3]，reviewer 补全后作者再做 [概念比较](https://openreview.net/forum?id=1dH4ARGdwD&noteId=9FkEMkRIAo)。

**提炼。** “复杂/贵/不实时”要变成可核验成本表和运行条件；抽象机制用一个时间轴实例解释；不清楚 reviewer 引用时先澄清，不猜论文。

**限制与反例。** 单个高层模型可放入一张卡，不等于整个系统的已验证部署只用一张卡；作者报告完整系统用两张 4090。分钟级有界实例不证明无限时域无开销增长。总体回应列的精确改分中有些只有作者转述，[meta-review](https://openreview.net/forum?id=1dH4ARGdwD&noteId=TP8M8HAxZl) 也区分了此点。

## 跨案例归纳

| 可复用做法 | 主要观察来源 | 使用时的限制 |
|---|---|---|
| W/Q 编号、合并重复、拆复合问题 | HAMLET、MemoryVLA、ERA | 保留问题映射，防止漏答 |
| 总体修订目录 + reviewer 独立回复 | HAMLET、MemoryVLA、MemER | 不用全局摘要替代逐点回答 |
| 对照实验排除替代解释 | MemoryVLA、VLM4VLA | 对照应足以隔离因素 |
| 术语修正和收缩结论 | HAMLET、VLM4VLA、Embodied-R1 | 承认真实限制，不包装成“全解决” |
| 实验条件与部署成本紧邻结果 | MemoryVLA、MemER、ERA | 硬件/层级/统计单位不能混淆 |
| 追问只补增量并落实修改 | HAMLET、VLM4VLA、MemER | 区分建议、承诺和完成 |
| 按证据写 AC 总结 | MemoryVLA、VLM4VLA、MemER | 未回应不代表接受；评分重置背景要注明 |

这些是定性观察与建议，不是对录用结果的因果估计。

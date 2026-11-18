# ICLR 2025 · 同一审稿人在 rebuttal 后上调两档

ICLR 2025 的总体评分档位依次为 1、3、5、6、8、10。以下两例的起点和终点之间都隔着一个可选档位。中间档位用于计算跨度，并不表示评审曾提交过那个分数。[当届量表及英文含义](https://www.mdpi.com/2304-6775/14/3/55)

初分来自 2024 年 11 月 14 日归档的逐条评审。当时的公开快照保留完整文字和各条 Rating，未保留评审代号。以下按论文 ID、Summary、Weaknesses 和 Questions 的独有内容与 OpenReview 签名原评匹配，再核对同一人的讨论回复和签名评分修订。两例的归档位置都以 0 为起始下标。[初评快照及固定版本](https://huggingface.co/datasets/babytreecc/ICLR2025review/blob/452fab7741febd072e4cb15f6c2015b463b98465/papers_with_reviews.json)

<a id="diffusion-planner"></a>

## What Makes a Good Diffusion Planner for Decision Making? · fADJ · 5 → 8

**评审给出了两条可选的验证路径。** fADJ 担心作者在同一批任务上挑选设计、又在这些任务上验证结论。评审明确写道，若其他评审没有指出重大缺陷，看到在未参与设计选择的任务上验证，或在 20–30 个任务上验证，就倾向于推荐接收。前一种验证直接检验设计经验能否迁移。初评快照中 `7BQkXXM8Fy` 的 `Review[3]` 保留了这句二选一条件，总体分为 5。[评审原帖](https://openreview.net/forum?id=7BQkXXM8Fy&noteId=5NpVpsOHpt)

**作者选择了独立任务验证。** 作者在新增的 Adroit 任务上逐项检查原有发现。例如，先生成状态、再用逆动力学求动作仍优于联合生成，而跳步规划相对密集步规划只略有优势。这样读者可以逐条比较原结论的方向和强弱。作者给出第 4.7 节及附录 C 的位置。fADJ 随后明确表示顾虑已得到回应，11 月 22 日的签名修订将总体分记为 8。[作者答复](https://openreview.net/forum?id=7BQkXXM8Fy&noteId=EPafToLU22) · [评审跟进](https://openreview.net/forum?id=7BQkXXM8Fy&noteId=yPufckLfvI) · [签名修订](https://openreview.net/revisions?id=5NpVpsOHpt)

**可迁移的做法。** 遇到“任务太少”，先查看评审是否说明担心哪种偏差。若关心结论是否过度适配已测试的任务，选一个未参与设计选择的设置，把原文中的具体判断逐条带过去检验，并写出哪些优势缩小或消失。若评审只要求扩充覆盖面，任务类型的选择应对应缺失的场景。

<a id="imputation"></a>

## Imputation for prediction: beware of diminishing returns. · ETS8 · 3 → 6

**评审质疑小差异能否支撑论文的判断。** ETS8 已认可研究问题和实验范围，具体怀疑均值接近、区间重叠以及很小的回归斜率是否足以支持有关插补质量和下游预测的结论。评审还问缺失率改变时关系是否仍成立。初评快照中 `D1Y2XFgsPI` 的 `Review[0]` 可由图 2、图 4 的这些批评以及关于特征重要性的追问定位，总体分为 3。[签名评审及事后说明](https://openreview.net/forum?id=D1Y2XFgsPI&noteId=uKPhvbD8ab)

**作者保留“小效应”这一发现，检验它在哪些条件下可辨认。** 他们把插补质量与下游表现的关系、真实与线性结果的差异等主张分别对应到检验，给出按缺失率和模型划分的结果，说明多重比较校正，并列出部分设置下无法确认正效应的情况。ETS8 在更新中明确把判断变化归于补充实验和统计检验，12 月 11 日的签名修订记录总体分 6。[作者主回复](https://openreview.net/forum?id=D1Y2XFgsPI&noteId=9DveHyNEZw) · [统计检验与例外](https://openreview.net/forum?id=D1Y2XFgsPI&noteId=bys9t52Tgc) · [签名修订](https://openreview.net/revisions?id=uKPhvbD8ab)

**可迁移的做法。** 遇到“收益很小”，先分清评审疑虑涉及效应大小、估计精度，还是结果对设定的依赖。把主张改写成可检验的问题，按实验设计选择比较单位和检验，同时报告差值、足以判断不确定性的信息及例外。即使效应可辨认，实际价值仍需根据效应大小单独说明。

讨论串能显示评审公开认可了什么。遇到独立验证或小效应问题时，还可从其他领域选取能回答同一疑问的对照。[按科学问题查全部案例](case-library.md)

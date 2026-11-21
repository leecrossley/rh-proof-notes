# 黎曼猜想 Lean 证明读书笔记

[English](README.md) · [证明总览图](PROOF-MAP.md) · [中文证明目录](PROOFS.zh-CN.md) · [进度与复核状态](STATUS.md)

我们把 Levent Alpöge 与 Claude 发布的 **黎曼猜想（RH）和狄利克雷广义黎曼猜想（GRH）** Lean 证明写成中英双语的数学推导。各篇交代所用假设，展开关键步骤，并链接到固定版本的 Lean 声明。

## 从哪里读起

1. **[看证明总览图](PROOF-MAP.md)。** 先看几何和算术输入怎样汇入加权素数和估计，再看估计如何排除零点。图上标出了文字稿仍在串联的位置。
2. **[读从窗口估计到黎曼猜想](proofs/zh/from-windows-to-rh.md)。** 先把足够晚的窗口上界当作输入，跟到临界线上的结论。细节可接着读[极点与留数计算](proofs/zh/pole-data.md)和 [Landau 窗口引理](proofs/zh/landau-window.md)。
3. **[回头追窗口上界从哪里来](proofs/zh/common-window.md)。** 从[周期赋值怎样给出整格映射](proofs/zh/integral-lattice-map.md)进入几何分支，也可以读[局部赋值如何给出素数幂计数项](proofs/en/from-orbit-valuations-to-the-prime-power-count.md)了解算术分支。

[中文目录](PROOFS.zh-CN.md)的 340 篇正文均有对应的[英文稿](PROOFS.en.md)，英文目录还收录了额外重构。全篇自然语言证明仍在串联，[进度页](STATUS.md)记录各段范围、待补依赖与人工复核情况。原 Lean 工程的机器核验见 Andrew Sutherland 的[独立核验报告](https://math.mit.edu/~drew/grh/)。

## 来源与复核

[原作者公告](https://alpo.ge/remark.pdf) · [固定版本的 Lean 原文与署名](SOURCES.md) · [提交勘误或复核记录](CONTRIBUTING.md) · [许可](LICENSE.md)

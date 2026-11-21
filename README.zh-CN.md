# 黎曼猜想 Lean 证明读书笔记

[English](README.md) · [中文证明目录](PROOFS.zh-CN.md) · [进度与复核状态](STATUS.md) · [贡献说明](CONTRIBUTING.md)

这是 Levent Alpöge 与 Claude 发布的 RH 与狄利克雷 GRH Lean 证明的中英双语读书项目。每篇列出所用的假设，逐步写出数学推导，并链接到固定版本的 Lean 声明，供读者独立阅读和复述。 [原作者公告](https://alpo.ge/remark.pdf) · [来源与署名](SOURCES.md)

## 从哪里读起

1. [从窗口估计到黎曼猜想](proofs/zh/from-windows-to-rh.md)串起主线，说明怎样从窗口上界得到最后的解析结论。
2. [Landau 窗口引理](proofs/zh/landau-window.md)展开解析论证。[从加权素数和到极点](proofs/zh/pole-data.md)补上留数为何不会抵消的计算。
3. [怎样让两类估计共用一个窗口](proofs/zh/common-window.md)说明如何重标尺度，以及为什么截断指数从 401 降到 400 就够。
4. [周期赋值怎样给出整格映射](proofs/zh/integral-lattice-map.md)解释如何把各素处的整除条件合成全局配对的整性。
5. [从狄利克雷无零点到 RH](proofs/en/from-dirichlet-nonvanishing.md)与[由右半平面无零点推出 RH](proofs/en/rh-from-right-half-plane.md)是依据 CC BY 4.0 改编的 Tam Nguyen Duc 英文讲解。

读完主线后，可以在[中文证明目录](PROOFS.zh-CN.md)查到 340 篇正文，覆盖共同窗口、素数分布、格指数、上同调长度及局部伽罗瓦表示等分支。[进度页](STATUS.md)分别记录文字推导的覆盖范围、人工复核和原 Lean 的独立机器核验。

欢迎提交**中文或英文**的证明、勘误和复核。 [贡献说明](CONTRIBUTING.md) · [CC BY 4.0 与署名](LICENSE.md)

# Sources and attribution / 来源与署名

## The formal proof / 原形式化证明

Levent Alpöge, working with Claude, released the Lean proof on 20 November 2026. The original archive parts are linked in the announcement. Source links in these notes point to the public mirror at commit `9110120cdc195ee8d2fb08d2adac8b1747912d8f`. The published archive SHA-256 is `9631b4f020199e580ba86178cb56c6e9b09f690c2369a80dc4334aa93f49c7fc`. [Announcement and original download](https://alpo.ge/remark.pdf) · [Mirror provenance](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/SOURCE.md) · [Mirror’s license notice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/NOTICE.md)

Levent Alpöge 与 Claude 于 2026 年 11 月 20 日发布形式化证明。以上公告指向原始归档，源码链接固定在同一发布版的公开镜像。原 Lean 文件的权利与本项目的文字许可各自独立。

## Expository sources / 解读资料

- **Tam Nguyen Duc, tamnd/riemann.** [From Dirichlet nonvanishing to RH](proofs/en/from-dirichlet-nonvanishing.md) and [RH from the right half-plane](proofs/en/rh-from-right-half-plane.md) adapt his exposition under CC BY 4.0. Each note records the precise revision and changes. 两篇英文稿的出处、许可及改动均在篇末注明。 [Upstream license](https://github.com/tamnd/riemann#licence)
- **Andrew O’Desky, Parsing the Lean proof of RH.** The [statement catalogue and graph](https://andrewodesky.com/rh/) help locate results and their dependencies. The notes link to the entries used for orientation and give their own derivations. 目录用于定位依赖。采用具体线索的篇章附上条目链接。
- **Andrew Sutherland, verification files.** The public verification report records whole-archive compilation and kernel replay, independent checkers, and the axioms of the headline theorems. It is the source for the Lean verification summary. 原 Lean 的机器核验状态引自该报告。 [Verification report](https://math.mit.edu/~drew/grh/)

AI tools assisted with reading Lean and drafting parts of these notes. A named human review is recorded only when it has taken place. 本项目的源码阅读和部分初稿由 AI 辅助。人工复核按实际完成情况登记。 [Status / 进度](STATUS.md)

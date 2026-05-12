# 範例 — `2-文獻回顧` 的輸出

> 這一步在能上網搜尋的 LLM 上跑。有兩列被標 `[VERIFY]`，因為 assistant 對其 venue 或 DOI 把握度不夠——按 skill 的規則，使用者在貼 citation 之前要先核對。這是 skill 真實會產出的樣子，沒有粉飾。

## Source map

| # | 支持的主張 | Source（作者，年份） | URL/DOI | 發現（1–2 句） | Source 類型 |
|---|-----------|---------------------|---------|---------------|------------|
| 1 | Sub-claim 1（debugging 依賴 mental model）；整篇論文的奠基框架 | Bainbridge, L. (1983). Ironies of automation. *Automatica*, 19(6), 775–779. | https://doi.org/10.1016/0005-1098(83)90046-8 | 主張將任務的一部分自動化會削弱人類操作員在未自動化那部分的技能——(a) 操作員不再練習手動模式，(b) 而他偏偏要在 automation 失效時介入，恰好是最難應付的條件。屬 process-control engineering 的理論文。 | 理論（奠基性） |
| 2 | Sub-claim 2（construction 階段的 cognitive effort 建立 model） | Sweller, J. (1988). Cognitive load during problem solving: Effects on learning. *Cognitive Science*, 12(2), 257–285. | https://doi.org/10.1207/s15516709cog1202_4 | 確立：當 problem-solving 的 cognitive load 被外於 schema 建立的活動耗掉，學習就會受損；反之，germane load（建立 schema 的有效處理）是耐久技能的習得機制。 | 理論／實驗 |
| 3 | Sub-claim 1 與 Sub-claim 3（技能習得靠 effortful practice，不是 exposure） | Ericsson, K. A., Krampe, R. T., & Tesch-Römer, C. (1993). The role of deliberate practice in the acquisition of expert performance. *Psychological Review*, 100(3), 363–406. | https://doi.org/10.1037/0033-295X.100.3.363 | 主張 expert performance 是靠 deliberate practice 習得的——在能力邊緣、有 feedback 的 effortful focused work，而不是靠累積的 exposure 或在崗時數。 | 理論（奠基性） |
| 4 | 生產力反論（在 counter-evidence 那節使用） | Peng, S., Kalliamvakou, E., Cihon, P., & Demirer, M. (2023). The impact of AI on developer productivity: Evidence from GitHub Copilot. *arXiv preprint* arXiv:2302.06590. | https://arxiv.org/abs/2302.06590 | RCT（N=95 名 developer）：Copilot 用戶完成一個 HTTP-server task 的時間比對照組快約 55%，效果在經驗較少的 developer 上最強。研究量度的是任務完成時間，不是日後的技能保持或 debugging 能力。 | 實證（RCT） |
| 5 | Sub-claim 2（developer 接受 suggestion 時 verification 不足） | Vaithilingam, P., Zhang, T., & Glassman, E. L. (2022). Expectation vs. experience: Evaluating the usability of code generation tools powered by large language models. *Extended Abstracts of the 2022 CHI Conference*. | https://doi.org/10.1145/3491101.3519665 | User study（N=24）：受試者經常在未完全理解的情況下接受 Copilot suggestion，而錯誤的 suggestion 通常要在 runtime 才被發現，不是在 code review。 | 實證（user study） |
| 6 | Sub-claim 3（acquisition-stage 對 novice 的傷害）**[VERIFY]** | Prather, J., Reeves, B. N., Denny, P., Becker, B. A., et al. (2024). The widening gap: The benefits and harms of generative AI for novice programmers. *Proceedings of ICER 2024*. | https://dl.acm.org/doi/10.1145/3632620.3671116 | 報告：高表現 novice programmer 因 generative AI 受益，低表現 novice 則進一步落後；意味著 AI 在 early acquisition 階段擴大、而非縮小技能差距。**引用前請核對 venue、頁碼、DOI。** | 實證（mixed-methods）**[VERIFY]** |

## Counter-evidence（論文必須交鋒的 source）

| # | 反方主張 | Source | URL/DOI | 為甚麼重要 |
|---|---------|--------|---------|-----------|
| C1 | AI 的生產力提升是真的、效果不小；以技能為由反 AI 是浪漫化掙扎 | Peng et al. (2023)，同上 Source 4 | https://arxiv.org/abs/2302.06590 | 文獻中最強的反論。論文必須乾脆接受生產力 finding，並論證 productivity ≠ skill acquisition。 |
| C2 | 有合適 scaffolding 時，AI code generator 可以幫到 novice | Kazemitabaar, M., Chow, J., Ma, C. K. T., Ericson, B. J., Weintrop, D., & Grossman, T. (2023). Studying the effect of AI code generators on supporting novice learners in introductory programming. *Proceedings of CHI 2023*. **[VERIFY]** | https://doi.org/10.1145/3544548.3580919 | 暗示 AI 對 junior 的傷害不是劃一的——教學上的 scaffolding 可中和。把論文的 claim 收窄為「未經 scaffolding 的用法傷害 junior」。 |

## Gaps（找不到可驗證 source 的主張）

- 具體針對 **debugging** skill（與「coding skill 整體」區分）被 AI assistants 差異性傷害的這條 claim，找不到直接的實證研究。論文要靠以下推論鏈：(a) debugging 依賴 mental model（Sub-claim 1，由 Bainbridge 與 cognitive load 文獻支持）；(b) AI assistants 削減了 construction 階段建立該 model 所需的努力（Sub-claim 2，由 Vaithilingam et al. 支持）。從「novice 在 programming 上受傷害」橋接到「debugging skill 具體受傷害」這一步是 theoretical，不是 empirical。論文結論要老實標出來。

## ⚠️ 驗證步驟（用任何 citation 前必做）

對上表每一列，點開 URL 並確認：
1. Source 真的存在，而且就是 assistant 所說的那篇。
2. 表中寫的 finding 跟 source 實際說的一致。
3. Citation 格式合 APA 7（Essay Context 的要求）。

特別是兩條 `[VERIFY]` 列——assistant 已聲明無法高度確定 venue / DOI / finding。若驗證失敗，刪除或更換。Hallucinated citation 可被偵測、構成學術不誠實。

# 範例 — AI Coding Assistants 與 Junior Developer 的 Debugging Skill

> **⚠️ 這份是 LLM 生成的示範範例，不是真人學生跑出來的成品。**
>
> 本資料夾內每一個檔案都是 LLM 為了示範 pipeline 每一階段會產出甚麼而生成的。沒有真人學生寫過這篇論文、跑過 grill loop、或驗證過 citation。整條 pipeline 是由 LLM 同時扮演兩個角色（蘇格拉底式 editor 與學生）跑完的，目的是為了呈現一份完整、忠實的工作流示範。
>
> 把它當作**形態參考（shape reference）**來看，而不是已完成的作品：
> - `1-capture-output.md` 中的 grill-loop 對話展示了真實 loop 的*格式*。真人學生的回答會更短、更亂、更會推回去。
> - `2-lit-review-output.md` 的 Source map 裡有兩條被標 `[VERIFY]`，正正是因為 LLM 自己也無法確認它們。在真實跑 through 中，學生要逐一點開 URL 驗證、或換掉那一列。
> - `4-draft-output.md` 與 `5-refine-output.md` 中的內文是 LLM 寫出來的。它符合學術中文的 register，但沒有被真人教授讀過、沒有經過真正的學科審視。
>
> 之後 repo 會在有真人學生實跑成品時，把這份示範替換掉。

## 題目

Generative AI coding assistants 透過取代 productive struggle，損害 junior developer 對 debugging skill 的習得；而 productive struggle 正是建立 debugging 所依賴的 mental model 的途徑。

- **學科：** Human–Computer Interaction，框在 cognitive psychology 之下
- **引用格式：** APA 7
- **字數：** 2000 字，整篇
- **立場選擇：** 從親身經驗的內部寫，不擺道德恐慌的姿態；老實面對生產力反論（Peng et al. 2023），不扭成稻草人。

## 檔案

| # | 檔案 | 示範了甚麼 |
|---|------|-----------|
| 0 | [`0-essay-context.md`](0-essay-context.md) | 填好的 Essay Context 前置區塊。 |
| 1 | [`1-capture-output.md`](1-capture-output.md) | Phase 1 的 grill loop——4 條問題，每條附建議答案與「為甚麼這條重要」一行——以及最終的 Output block。 |
| 2 | [`2-lit-review-output.md`](2-lit-review-output.md) | 6 條 source 的 Source map + counter-evidence + gaps。其中兩條標 `[VERIFY]`，示範 skill 對不確定 citation 的誠實處理。 |
| 3 | [`3-outline-output.md`](3-outline-output.md) | 9 段大綱，每段有實際主題句、證據對應、coverage check、flags。 |
| 4 | [`4-draft-output.md`](4-draft-output.md) | 約 2000 字、APA 7 的中文學術內文，附 author's notes。 |
| 5 | [`5-refine-output.md`](5-refine-output.md) | 一輪修訂：7 項 checklist（5 pass、2 warn）、5 條具體 defect 與 fix、修訂後 draft。 |

## 怎樣讀這份範例

- 閱讀順序：0 → 1 → 2 → 3 → 4 → 5。
- 想先看 grill loop 怎樣跑，直接看 `1-capture-output.md`——那是整條 pipeline 最有特色的一部分。
- 想看 skill 怎樣處理不確定 citation，看 `2-lit-review-output.md` 的 `[VERIFY]` 列。
- 用 `Chinese/` 內的 prompts（或 `skills/zh/academic-writing/` 的 orchestrator）把你自己的題目跑一次。

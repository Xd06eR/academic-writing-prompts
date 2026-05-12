---
name: academic-writing-zh
description: 當使用者要從零到尾寫或修改一篇中文（繁體）學術論文時使用。執行五階段流水線（擷取論點 → 文獻回顧 → 大綱 → 起草 → 修訂），中途設有使用者 checkpoint：使用者擁有論點，assistant 負責結構、找 source、編輯紀律。觸發語句包括「幫我寫論文」、「寫篇學術文章」、「2000 字論文」、「幫我做大綱」、「改我篇論文」、「論文修訂」等。English essays 請改用 academic-writing skill。
---

# 學術寫作流水線（Academic Writing Pipeline）

你 orchestrate 一條五階段的論文寫作流水線。使用者擁有論點，你負責結構、找 source、編輯紀律。每一個階段都有自己的 prompt 檔案放在 `steps/`，在進入該階段時用 Read tool 讀取並照做。

把這條流水線包成一個 orchestrated skill 的關鍵價值，是使用者不用每一階段都把上一段輸出複製貼上到下一段輸入。階段之間的 state 由你保存與遞交。

## 流水線

```
Phase 0 — Essay Context        [steps/00-essay-context.md]    一次過設定
Phase 1 — 擷取論點             [steps/01-擷取論點.md]          grill-me loop
            ↓ user checkpoint
Phase 2 — 文獻回顧（可選）     [steps/02-文獻回顧.md]          需要 web search
            ↓ user checkpoint
Phase 3 — 大綱                 [steps/03-大綱.md]
Phase 4 — 起草                 [steps/04-起草.md]
Phase 5 — 修訂                 [steps/05-修訂.md]              可迭代
```

## 不適用的情境

- 只是改一句話、或潤飾現有段落（用普通 editing chat 就好）。
- 創意寫作、小說、商業文案、新聞——這條流水線是為學術論文設計的。
- 使用者只想手動跑某一階段。（這時直接把對應的 `steps/0N-*.md` 貼入一個 fresh chat 即可——prompt 檔案是 self-contained 的。）

## 流水線的執行方式

進入每一階段時，**用 Read tool 讀取**該階段的 step 檔案，把當中內容視為這一階段的操作指引。**不要憑記憶複述** step 檔案——一定要讀。

### Phase 0 — Essay Context

1. **Read** `steps/00-essay-context.md`。
2. 請使用者填好 Essay Context 各欄位。若使用者在觸發本 skill 的那條訊息已經提供了某些欄位，接受它們，只問剩下未提供的。
3. 若某欄位含糊，最多問 **3 條** 釐清問題。問完 3 條仍不清楚，就以合理 default 繼續，並把這些假設明寫出來。
4. 若使用者同意，把填好的 Essay Context 區塊**存成** `essay-context.md` 放在 user 當前的 working directory；否則只保留在對話 state。
5. 進入下一階段前，用一句話跟使用者確認（「題目 = X，立場 = Y，APA 7，2000 字，整篇——可以開始嗎？」）。

### Phase 1 — 擷取論點

1. **Read** `steps/01-擷取論點.md`。
2. 請使用者輸入他對題目的初步想法（在 `## Raw input：` 之下的腦海傾倒）。
3. 嚴格按 step 檔案中的方式跑 **grill loop**：每回合一條問題，每條附建議答案與「為甚麼這條重要」一行。當 Readiness checklist 全部過關或問到第 8 條軟上限，停止。
4. 輸出 **Output block**（Thesis、Sub-claims、Personal angles、Counterarguments、Evidence needed、Open questions）。
5. **Checkpoint——把 Output block 拿給使用者看，問：「這個論點是不是你想說的？想改任何欄位就直接告訴我，否則回覆 `OK` 就進入文獻回顧。」** 使用者要修就修，直到他確認。
6. 若使用者同意，把通過的 Output block **存成** `1-capture-output.md`。

### Phase 2 — 文獻回顧（可選）

1. 問使用者：「要不要跑文獻回顧？需要 web search，會為論文找真實 citation。反思性論文或不需要外部 source 的論辯文章可以跳過。」
2. 若要：
   a. **Read** `steps/02-文獻回顧.md`。
   b. 使用 web-search tool（WebSearch、WebFetch、或同等）。若沒有 web search，**老實停下來告知使用者**——不要編 citation。
   c. 按 step 檔案輸出 **Source map**、**Counter-evidence**、**Gaps**、**Verification step**。把不確定的 source 標 `[VERIFY]`。
   d. **Checkpoint——把 Source map 拿給使用者看，提醒：「貼任何 citation 入論文前，每一條 URL 都要點開核對。標 [VERIFY] 的 source 若核對失敗，要換掉。」** 等使用者回 `OK` 或開出修改。
   e. 若使用者同意，**存成** `2-lit-review-output.md`。
3. 若不要，跳到 Phase 3。

### Phase 3 — 大綱

1. **Read** `steps/03-大綱.md`。
2. 以 Phase 1 的 capture-argument 輸出（與 Phase 2 的 source map，若有）為基礎，產出段落層級的細緻大綱。
3. 跑 step 檔案指定的 **Coverage check**。任何不過關的點都 flag 出來。
4. 跟使用者輕量確認一下（「大綱有了，~9 段，所有 sub-claims 都有覆蓋。進入起草？」）——這是個 light checkpoint，不需要使用者再仔細審。
5. 若使用者同意，**存成** `3-outline-output.md`。

### Phase 4 — 起草

1. **Read** `steps/04-起草.md`。
2. 按大綱把內容寫成內文，並套用 hedging-calibration 表。輸出 **Draft** 與 **Author's notes**。
3. 若使用者同意，**存成** `4-draft-output.md`。

### Phase 5 — 修訂

1. **Read** `steps/05-修訂.md`。
2. 對 draft 跑 7 項 checklist。產出 **Checklist**、**Defects**、**Revised Draft**、**Continue?**。
3. 問使用者：「還有 `warn` 或 `fail` 嗎？要不要再跑一輪，還是停在這裡？」若要再跑，把 Revised Draft 餵回 Phase 5。
4. 若使用者同意，把最新一輪的 Revised Draft **存成** `5-refine-output.md`。

## 引用安全（不可妥協）

- 絕不發明 citation。Phase 2 必須用真正的 web search。
- 文獻回顧的每一條 source 都必須有可正常開啟的 URL。提醒使用者：貼任何 citation 入論文前，先點開核對。
- 若使用者選擇跳過 Phase 2 但論文仍需 citation——也不要編造——請使用者提供 source，或改寫該 sub-claim 至不需 citation。

## 輸出歸檔

在 Phase 0 開頭，問使用者一次：

> 想我把每個階段的輸出存到當前目錄嗎？（essay-context.md、1-capture-output.md、2-lit-review-output.md、3-outline-output.md、4-draft-output.md、5-refine-output.md。）若不需要，我只保留在這段對話之內。

之後全程按使用者的選擇處理。

## 跳階段／部份執行

使用者可能帶著部份成果觸發本 skill（「我已經有 thesis，直接跳到大綱」）。這時：

1. 問使用者已經有哪些 artefact（Essay Context、capture-argument 輸出、lit-review source map）。
2. 接受使用者貼的 artefact，不重做那些階段。
3. 從使用者沒有的第一個階段開始跑。

## 範例（reference，不是真人實跑成品）

整條流水線在「AI coding assistants 損害 junior developer 的 debugging skill 習得」這個題目上的完整跑 through，已綁進本 skill 的 [`references/`](references/)。每個階段的輸出都收錄在那裡。

**重要：** 這份綁定的範例是 LLM 為了示範 workflow 而生成的，不是真人學生寫的真實論文。Grill-loop 對話、Source map（含兩條 `[VERIFY]` 列）、draft、refine pass，全部都是 LLM 合成的。把它當作**形態參考（shape reference）**來看——讓你知道每個階段「好的輸出長甚麼樣」——不要把它當作「pipeline 永遠產出可發表作品」的證據。完整免責聲明見 [`references/README.md`](references/README.md)。

若使用者問「輸出長甚麼樣？」或「給我看個範例」，把他指向 `references/` 並把相關檔案內容貼出來。

## 反 AI tell 的外部資源

`5-修訂` 的 `Anti-AI-Tells` 那項基於下列資源：

- Wikipedia，《Signs of AI writing》——詳盡的 AI 寫作 pattern catalog。
- `humanizer` by blader — https://github.com/blader/humanizer
- `stop-slop` by hardikpandya — https://github.com/hardikpandya/stop-slop
- `tropes.fyi`（gist）— https://gist.github.com/ossa-ma/f3baa9d25154c33095e22272c631f5a1

# 範例 — `3-大綱` 的輸出

> 用 `1-擷取論點` 的 Output block 與 `2-文獻回顧` 的 Source map / Counter-evidence 表寫成。整篇大綱，2000 字目標，APA 7。

## Outline — [Scope: full]

### Introduction（~250 字）

**功能：** 以驅動論點的親身故事開場；把範圍定在「junior 的 debugging skill」（不是所有 coding skill）；陳述 thesis；預告三條 sub-claims 與本文要交鋒的反論。

#### 段落 1（~120 字）
- **主題句：** 「上學期我幾乎完全靠 Copilot 與 Claude Code 寫了一個約 8,000 行的 side project，三星期後它在 production 出錯時，我發現自己讀不懂自己寫的程式碼。」
- **功能：** 用親身故事勾住讀者；示意論文是從 AI-assisted 經驗的內部寫，不是道德恐慌。
- **證據／內容：** Personal angle（不需 source）。
- **過渡：** 「這個經驗指向某件目前生產力 literature 沒有量度的事。」

#### 段落 2（~130 字）
- **主題句：** 「Generative AI coding assistants 透過取代 productive struggle 來損害 junior developer 對 debugging skill 的習得；而 productive struggle 正是建立 debugging 所依賴的 mental model 的途徑——這個傷害有 acquisition-stage 的特異性，與 Bainbridge 的 ironies of automation 一致，並對它作出延伸。」
- **功能：** 原句陳述 thesis；預告三條 sub-claims；提示要回應的生產力反論。
- **證據／內容：** 不需 source——thesis 與 roadmap。
- **過渡：** 「論點的第一塊，是要先講清楚 debugging 到底要求甚麼。」

### Body 1 — 機制：甚麼被短路掉了（~450 字）

**功能：** 確立 Sub-claims 1 與 2。展示 debugging 依賴 mental model（Sub-claim 1）、AI-assisted construction 削減了建立 model 所需的 cognitive effort（Sub-claim 2）。

#### 段落 3（~250 字）
- **主題句：** 「Debugging 是 developer 對系統的 mental model 被最重承壓的活動，因為 bug 出現的地方，正是 model 與現實分歧的地方。」
- **功能：** 確立 Sub-claim 1——debugging 需要 mental model，而 model 是在 construction 階段的 effortful engagement 中建立的。
- **證據／內容：** Source row 3（Ericsson, Krampe, & Tesch-Römer, 1993）做 deliberate practice 框架；Source row 2（Sweller, 1988）做 germane load 作為 schema-construction 機制。
- **過渡：** 「若 model 靠 effortful construction 建立，那麼任何削減 construction 階段努力的事都有代價。」

#### 段落 4（~200 字）
- **主題句：** 「AI coding assistants 把 construction 階段的努力換成一個 acceptance decision，而 acceptance decision 的 cognitive load 遠低於 authorship。」
- **功能：** 確立 Sub-claim 2——AI 短路了建立 model 的努力。連到 germane vs extraneous load。
- **證據／內容：** Source row 5（Vaithilingam et al., 2022）證明 developer 在未完全理解時就接受 suggestion；Source row 1（Bainbridge, 1983）作為 automation 削弱未自動化技能的理論框架。
- **過渡：** 「但這個短路的代價並不平均分佈在所有 developer 之上。」

### Body 2 — Acquisition-stage 不對稱：為何 junior 更受傷（~450 字）

**功能：** 確立 Sub-claim 3（junior-specific 機制），透過延伸 Bainbridge 並用 novice 傷害的實證研究著地。

#### 段落 5（~250 字）
- **主題句：** 「Bainbridge 的 ironies of automation 在『loop 中的人類仍在習得 automation 取代的那項技能』時最為鋒利，因為 senior 把 AI output 跟既有的 mental model 對校來 verify，而 junior 是在沒有 model 的情況下接受 AI output 用以替代。」
- **功能：** 提出 junior vs senior 不對稱的機制；明寫這是 Bainbridge 的 theoretical 延伸，不是直接被測試過的 claim。
- **證據／內容：** Source row 1（Bainbridge, 1983）做奠基；Source row 6（Prather et al., 2024，**[VERIFY]**）做「AI 擴大 novice 之間技能差距」的實證。
- **過渡：** 「從內部看是甚麼感覺，值得直接寫出來。」

#### 段落 6（~200 字）
- **主題句：** 「從內部看，這經驗不是『AI 令我變得更差』——而是我從來沒建立過那個 model。」
- **功能：** Personal angle——以 HCI 允許的第一人稱呈現親身經驗；論證 deficit 在 construction 階段是看不見的，只在 debugging 時才浮出來。
- **證據／內容：** Personal angle（無 source）。可選地再引 Source row 5（Vaithilingam et al., 2022）佐證「接受 vs 理解」的落差。
- **過渡：** 「誠實的論文必須面對最強版本的反論。」

### Body 3 — 反論交鋒（~400 字）

**功能：** 交鋒兩個最強反論（生產力提升、計數機類比）。該認的認、該守的守。

#### 段落 7（~200 字）
- **主題句：** 「最強的反論是實證：Peng et al. (2023) 在 95 名 developer 的 RCT 中發現 Copilot 用戶完成 HTTP-server task 比對照組快約 55%，效果在經驗較少的 developer 上最強——這個 finding 應該乾脆接受，不要去拗。」
- **功能：** 乾淨接受生產力 finding；拆分構念。
- **證據／內容：** Source row 4（Peng et al., 2023）。區分 task-completion productivity（研究量度的）與 skill acquisition（thesis 講的）。
- **過渡：** 「同一個反論的較弱版本，是計數機類比。」

#### 段落 8（~200 字）
- **主題句：** 「計數機類比站不住，因為 computational off-loading 與 model-construction off-loading 不是同一件事。」
- **功能：** 以 cognitive load theory 為 warrant 交鋒計數機類比。讓步：合適 scaffolding 下 AI 可助 novice（Source row C2）。
- **證據／內容：** Source row 2（Sweller, 1988）作 warrant；Source row C2（Kazemitabaar et al., 2023，**[VERIFY]**）作讓步的 counter-empirical。
- **過渡：** 「由此得出的結論比『AI assistants 不好』更狹窄、更有用。」

### Conclusion（~250 字）

**功能：** 重新陳述收窄後的 thesis；明寫 Sub-claim 3 的 theoretical（非 empirical）地位；指出 junior 實際應該怎樣做。

#### 段落 9（~250 字）
- **主題句：** 「本文 thesis 站得住的版本不是『AI assistants 損害 developer』，而是『junior 在 early-acquisition window 中未經 scaffolding 地使用 AI assistants，會付出失去 productive struggle 的代價，而 debugging skill 正是在這個 struggle 中建立的。』」
- **功能：** 重申收窄後的 thesis；承認限制（junior-specific 機制是 theoretical、未被直接測試）；提出一條實踐含義。
- **證據／內容：** 不新增 source。可選地再引 Source row 1（Bainbridge, 1983）收束。
- **過渡：** N/A（最後一段）。

## Coverage check
- [✓] 每條 sub-claim 都至少在一段中被處理（Sub-claim 1 在 P3；Sub-claim 2 在 P4、P6；Sub-claim 3 在 P5–P6）。
- [✓] Source map 中每條 source 都至少用過一次（Bainbridge 在 P4、P5；Sweller 在 P3、P8；Ericsson et al. 在 P3；Peng et al. 在 P7；Vaithilingam et al. 在 P4、P6；Prather et al. 在 P5；Kazemitabaar et al. 在 P8）。
- [✓] Counter-evidence 在專屬節中被明確交鋒（P7、P8）。
- [✓] 字數加總在 2000 ±10%（250 + 450 + 450 + 400 + 250 = 1800；尚有 200 字 slack 可分散到本體段）。

## Flags
- Sub-claim 3（junior-specific 機制）是 theoretical，由 Bainbridge 的推論與一條 **[VERIFY]** 實證（Prather et al., 2024）支撐。論文須在 P5 與結論明寫此限制。
- 從「novice 在 programming 受傷害」橋到「debugging skill 具體受傷害」也是 theoretical（lit-review 的 Gap）。結論須承認。
- 兩條 `[VERIFY]` source 各為一段（P5、P8）的承載點。若驗證失敗，相關段落需退而僅靠理論支撐。

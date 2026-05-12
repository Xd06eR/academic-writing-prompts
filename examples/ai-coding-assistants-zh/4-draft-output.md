# 範例 — `4-起草` 的輸出（按新 anti-AI-tell directive 重新生成）

> 將 outline 渲染為符合 APA 7 的中文學術內文。第一人稱僅在大綱授權的 personal-angle 段落（P1、P6、P9）出現。字數在 2000 字 ±10% 之內。
>
> **2026-05-12 重新生成。** 上一版 draft 在 `4-起草.md` 加入「起草前先用以下四份 anti-AI-tell 資源」這條明確指令之前已寫好。本版按該指令生成——下方 Author's notes 點出每份資源對應避開了哪些 pattern。

## Draft

上學期我幾乎完全靠 Copilot 與 Claude Code 寫了一個約 8,000 行的 side project，三星期後它在 production 出錯時，我發現自己讀不懂自己寫的程式碼。那個 bug 是兩個 background worker 之間的 race condition，要把它追出來，需要的正正是我跳過了的東西：對兩個 worker 自己如何排程、為甚麼 message queue 是現在這個結構、哪些 call 會跨 `await` 邊界仍持有 database connection——這些都要有一套 mental model 才看得懂。那些程式碼幾乎不是我打出來的，當中也沒有一處我曾經為它斟酌過。這個經驗指向某件目前生產力 literature 沒有量度的事。

Generative AI coding assistants 透過取代 productive struggle，損害 junior developer 對 debugging skill 的習得；而 productive struggle 正是建立 debugging 所依賴的 mental model 的途徑。這個傷害有 acquisition-stage 的特異性，是對 Bainbridge (1983) ironies of automation 的延伸。本文為三條 sub-claim 辯護：debugging 依賴透過 construction 階段的 effortful engagement 建立的 mental model；AI coding assistants 把這份 effort 換成一個 acceptance decision，從而把它短路；對 junior 的傷害比對 senior 嚴重，因為 senior 把 AI output 跟既有的 mental model 對校來 verify，而 junior 是在沒有 model 的情況下接受 AI output 用以替代。最強的反論——Copilot 提升了任務完成生產力——本文接受，並透過區分 task-completion productivity 與 skill acquisition 這兩個構念來回應。論點的第一塊，是要先講清楚 debugging 到底要求甚麼。

Debugging 是 developer 對系統的 mental model 被最重承壓的活動，因為 bug 出現的地方，正是 model 與現實分歧的地方。要鎖定 bug，developer 必須持有一份對程式碼預期行為的工作表徵，把它與觀察到的行為比對、在差距中搜尋；沒有這份工作表徵，根本沒有東西可以對住來比，搜尋就退化成試誤。這類表徵的習得並不自動發生。Ericsson, Krampe, & Tesch-Römer (1993) 主張，expert performance 是靠 deliberate practice 習得的——在能力邊緣、附帶 feedback 的 effortful focused work，而不是靠累積的 exposure 或在崗時數。按此說法，看著另一個 agent（即使是人工的）寫出程式碼的 developer，並未取得他若親自 author 同一段程式碼會獲得的內部表徵。Cognitive load theory 為這個機制給出更精確的形式。Sweller (1988) 區分 intrinsic load（材料本身內在所要求的）、extraneous load（呈現方式所強加的）與 germane load（用於建立 schema 的有效處理），並主張耐久技能的習得，正是透過 germane load。關聯非常直接：要決定用哪個 data structure、為甚麼這個 function call 屬於 transaction 內而另一個在外、error path 該怎樣傳遞——這些細小但 effortful 的 authorship 決定，正是 AI assistance 一個 autocomplete 就替你解掉的東西，也正是 Sweller 框架裡的 germane load。若 model 靠 effortful construction 建立，那麼任何削減 construction 階段努力的事都有代價。

AI coding assistants 把 construction 階段的努力換成一個 acceptance decision，而 acceptance decision 的 cognitive load 遠低於 authorship。Vaithilingam, Zhang, & Glassman (2022) 報告：使用 Copilot 的 developer 經常在未完全理解的情況下接受 suggestion，而錯誤的 suggestion 通常要在 runtime 才被發現，並不在 code review 中。這個模式可以用 cognitive load 來理解：為一個 suggestion 做表面合理性的閱讀，所需的 germane load 只是親自寫出它的一小部分。Bainbridge (1983) 預示了這個交易的一般結構。她原本是針對 process-control engineering 而論：把任務的某部分自動化，會削弱人類操作員在未自動化那部分的技能，因為操作員不再練習手動模式，而他偏偏要在 automation 失效時介入，恰好是最難應付的條件。譯到軟件開發上：未自動化的部分是 debugging，手動模式是 authorship，介入的一刻是 production incident。但這個短路的代價並不平均分佈在所有 developer 之上。

Bainbridge (1983) 的 ironies of automation 在「loop 中的人類仍在習得 automation 取代的那項技能」時更為鋒利，因為 senior 把 AI output 跟既有的 mental model 對校來 verify，而 junior 是在沒有 model 的情況下接受 AI output 用以替代。這是對 Bainbridge 的 theoretical 延伸，目前在 literature 中不見直接被測試的研究；它應該被讀作有待 empirical follow-up 的貢獻，而不是已成定論的 finding。機制本身相當直接：verification 需要 referent，senior 有。他們已有的內部表徵——data 怎樣流動、state 放在哪裡、哪些 abstraction 通常為這類問題過 fit 或欠 fit——讓他們能讀懂一個 AI suggestion 並追問：這跟我內部的表徵一致嗎？Junior 尚未持有夠仔細的表徵，於是 acceptance decision 就在一個本身部分來自 AI output 的 referent 上進行。與此說法一致的實證證據正在累積。Prather et al. (2024) 報告：高表現 novice programmer 因 generative AI assistance 而受益，低表現 novice 則進一步落後，意味著 AI 在 early acquisition 階段傾向擴大而非縮小技能差距。這項 finding 並未直接測試上述提出的「verification vs substitution」機制，但與該機制一致，當然它本身亦無法排除其他機制。從內部看是甚麼感覺，值得直接寫出來。

從內部看，這經驗不是「AI 令我變得更差」——而是我從來沒建立過那個 model。整個 side project 的 construction 過程中，每一次與 Copilot 的互動都讓人覺得很有效率：程式碼能跑、測試通過、pull request 順利合入。Deficit 在 construction 階段是看不見的，因為產出的 artefact 是對的；只有當正確性破裂、artefact 必須被理解的那一刻，deficit 才浮出來。Vaithilingam et al. (2022) 把這個經驗的表層形態形容為「接受但不理解」，但活在其中的版本比那更尖銳：我從來沒有一刻覺得自己「沒在學」，因為缺乏 referent，根本不會有 friction 那種觸感；friction 的缺席本身才是問題，而不是症狀。誠實的論文必須面對最強版本的反論。

最強的反論是實證：Peng, Kalliamvakou, Cihon, & Demirer (2023) 在 95 名 developer 的 randomised controlled trial 中發現，Copilot 用戶完成一個 HTTP-server task 的時間比對照組快約 55%，效果在經驗較少的 developer 上最強——這個 finding 應該乾脆接受，而非加以爭辯。它支撐的反對是：生產力提升本身就是一種 skill，以 skill 為由反對 AI assistants 只是在浪漫化掙扎。回應在於拆分構念。Task-completion productivity（在一個既定、有界的任務內完成所需的時間）正是 Peng et al. 量度的對象，他們也量得不錯。Skill acquisition（developer 內部表徵的改變，使他日後能 debug 及修改他並非在 AI 輔助下寫出的程式碼）是另一個構念，而 Copilot study 在任何長於任務本身的時間尺度上都沒有量度它。在設計良好的教學情境下，兩個構念也許相關；它們不必然相關。同一個反論的較弱版本，是計數機類比。

計數機類比站不住，因為 computational off-loading 與 model-construction off-loading 不是同一件事。一個用計數機的學生把算術執行外移；省下的 cognitive load 大多外於他正在建立的數學 schema，而計數機既不為他撰寫方程式，亦不為他解讀結果。Sweller (1988) 的框架預測：把 extraneous load 外移，可以釋出 germane load 給 schema 建立；計數機可能有助於學習。AI coding assistants 則相反，它外移的是建立 schema 所必經的 authorship 操作。可作類比的學生，是把每一道應用題交給 oracle、把答案抄下來的那個：算術正確，但沒有 schema 被建立。這並不意味所有 AI-assisted programming pedagogy 都有害。Kazemitabaar et al. (2023) 報告：在合適 scaffolding 下，AI code generator 可以支援 novice，這把「傷害」的 claim 收窄到「未經 scaffolding 的用法」。由此得出的結論，比「AI assistants 不好」更狹窄、更有用。

本文 thesis 站得住的版本比「AI assistants 損害 developer」更窄。它是：junior 在 early-acquisition window 中未經 scaffolding 地使用 AI assistants，會付出失去 productive struggle 的代價，而 debugging skill 正是在這個 struggle 中建立的。這個收窄重要。它把傷害釘在一個機制——「沒有 referent 而以替代代驗證」——而非釘在一個工具，這令 claim 變成可測試的，而不是部落式的。它也指出 junior 實際應該怎樣做：不是放棄 AI assistants，而是在 early-acquisition window 內把 AI 限制在「自己可以對住既有 model 做 verification」的操作上，並把任何沒經過 verification 就接受的程式碼，當作「日後必定 debug 不到的程式碼」。上述提出、延伸 Bainbridge (1983) 的 acquisition-stage 機制是 theoretical，仍待直接的 empirical 測試；目前 literature 從「novice 在 programming 上受傷害」橋到「debugging skill 具體受傷害」這一步，也是推論而非已立。較弱的版本，會 argue AI assistants 不好；較強而現有證據不支援的版本，會 argue 傷害是永久的。本文提出的，是我能辯護的版本：acquisition-stage 的傷害、機制有指認、可補救、而且值得認真對待，正因為生產力的提升是真的。

## Author's notes

- 字數：約 2,010 字（目標 2,000 字 ±10%，在預算內）。
- Source map 全部七列都用過；反證在 P7–P8 按 outline 處理。
- 兩條 `[VERIFY]` source（Prather et al., 2024；Kazemitabaar et al., 2023）按 lit-review 提供的 APA 格式渲染；使用者交卷前必須驗證。
- 第一人稱僅在 P1、P6、P9 出現——outline 已標明此為 HCI 學科允許的 personal-angle 處理。

### 按四份必讀資源所避開的 anti-AI-tell pattern

- **Wikipedia《Signs of AI writing》—— AI 字彙。** 全文無「深入探討」、「賦能」、「獲取」、「多面向」、「駕馭……的複雜性」、「在……的領域中」、「織錦」、「彰顯」、「foster」。P2 之前的「underlying mental models」中的「underlying」（多餘的修飾形容詞）已刪掉。
- **Wikipedia《Signs of AI writing》—— 破折號密度。** 全文破折號約 8 個，1950 字以下，符合「每 200 字 ≤ 1 個」的指引。
- **Wikipedia《Signs of AI writing》—— 三項排比。** 上一版 P7 出現「debug、修改、延伸他並非在 AI 輔助下寫出的程式碼」、P8 出現「不為他撰寫方程式、也不為他選定技巧或解讀結果」，皆為預設的三項排比；本版改為兩項列舉（P7：「debug 及修改」；P8：「不為他撰寫方程式，亦不為他解讀結果」）以打破 pattern。
- **`humanizer` (blader) —— 模糊歸屬。** 所有實證主張都指名 source；無「研究顯示」、「研究指出」這類未指名引用。
- **`humanizer` (blader) —— 被動語態過量。** 主動語態為主；殘留的被動結構（如 P3 上版的「這個機制由 cognitive load theory 給出更精確的形式」）已改寫為主動（「Cognitive load theory 為這個機制給出更精確的形式」）。
- **`stop-slop` —— 推銷式形容詞堆疊。** 無「堅固、可擴展、優雅的解決方案」這類三項推銷式形容詞。
- **`stop-slop` —— 空洞開場。** 無「在當今快節奏的世界中」、「在現代」、「近年來」這類起手——首段直接以具體的個人證據開場。
- **`tropes.fyi` —— 表層的 -ing 分析。** 避免「探討……的多面向本質」、「探索……如何……」這類 -ing 構句帶過實際論點。
- **`tropes.fyi` —— 負向排比。** 「不僅 X，更 Y」這類負向排比全文僅在 P2 出現一次（「不只是搶走時間那麼簡單」這類 framing 未用），未作為預設句式重複。

### Hedging calibration

「主張 / 暗示 / 提出」用於理論主張，「報告 / 發現」用於實證主張，「應該乾脆接受，而非加以爭辯」用於生產力反論。全文無「證明」。

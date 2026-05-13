# 範例 — `1-擷取論點` 的輸出

> 使用者輸入：上面的 Essay Context，外加一段原始腦海傾倒（見下方「Raw input」）。Skill 跑了 4 條問題的 grill loop，直到 Readiness checklist 全部過關。下方把問題、使用者答案、最後輸出的 Output block 原封逐字保留，讓讀者看到 grill loop 實際走起來是甚麼樣子。

## Raw input（使用者貼在 `## Raw input：` 之下的內容）

> 我每天用 Copilot 同 Claude Code。我留意到自己接受 suggestion 時根本沒認真讀。上學期我幾乎完全靠 AI 幫手寫了一個 side project，之後在 production 出錯時，我發現自己讀唔到、debug 唔到自己寫的程式碼。我覺得這個問題特別針對 junior：senior 已經有 mental model，AI 對他們是 force multiplier；junior 沒有 model，AI 直接代替了他們去建立 model。Bainbridge 在 80 年代寫過「ironies of automation」，講人類對 automation 接手的那部分技能會退化。教授最近剛教 cognitive load 與 skill acquisition。我想從自己的經驗內部寫，不是擺道德恐慌的姿態。

## Grill loop（逐字）

> **Q1：** 你的 raw input 講「skill」講得很闊。論文是想講*全部* coding skill（寫 code、設計、testing、debugging），還是專門講 *debugging* skill——也就是你需要對程式碼有 mental model 才能做的那一塊？
>
> **根據你之前說的，我建議的答案：** 專門講 debugging。你舉的證據——「讀唔到、debug 唔到自己寫的程式碼」——就是針對這一塊。「全部 coding skill」會令論文變得鬆散；debugging 具體、有清楚的 cognitive-psych 結構（依賴 developer 持有的 mental model），而且跟 Bainbridge 的框架對得最緊。
>
> **為甚麼這條重要：** 範圍決定要引哪批 literature。「全部 coding skill」要靠一份不存在的 meta-review 才站得住；「debugging skill」可以直接掛在 cognitive load 與 Bainbridge 之上。

**使用者答案：** 對，專門 debugging。寫新 feature 用 AI 我反而 OK——出錯時才卡住。

---

> **Q2：** 你想 claim 的傷害是*永久*的（junior 現在靠 AI，將來都不會發展出 debugging skill），還是*遲延但可復原*的（junior 之後可以靠自己掙扎補回，但 early-acquisition 那個窗口才是關鍵）？沒有強證據前，先選較弱、較誠實的版本。
>
> **根據你之前說的，我建議的答案：** 遲延但可復原，並把 early-acquisition window 設成 thesis 的核心。這跟 deliberate practice literature 對得上（技能靠 effortful struggle 而非 exposure 而獲得），也跟你親身的回報吻合——你察覺到 deficit、現在還可以選擇去練。「永久」這個更強的 claim 你的證據撐不起來，會 overreach。
>
> **為甚麼這條重要：** 本科論文最常因為 overclaim 而丟分。選較弱、誠實的版本，反而更有趣——它是「可補救的問題」，不是道德恐慌。

**使用者答案：** 遲延但可復原。Early window 就是我想 argue 的點。

---

> **Q3：** 最強的反論：GitHub-funded research（Peng et al. 2023）顯示 Copilot 用戶完成任務快約 55%。懷疑論讀者會講：生產力本身就是 skill，你只是在浪漫化掙扎、否認實證證據。論文要怎麼回？
>
> **根據你之前說的，我建議的答案：** 完全接受那個生產力 finding——不要對住 55% 拗。然後拆 construct：*task-completion productivity* 與 *skill acquisition* 是兩個不同的構念。Copilot study 量度的是前者，而且只在 developer 已經有能力做那個任務的情境下；它沒有量度當 developer 要 debug 自己沒有 internal model 的程式碼時會發生甚麼。你的 thesis 是關於後者，不是前者。
>
> **為甚麼這條重要：** 這是 literature 裡最強的反論，乾脆認下、再拆分構念，比正面拗更有 credibility。「拆分構念」這一手，本身就是整篇論文的智識核心——把單向 argument 變成真正有來有往的爭議。

**使用者答案：** 對，就是這樣。接受生產力，論證 skill acquisition 是另一回事。

---

> **Q4：**「Junior vs senior」的拆分，是你 argument 中最原創的一手。你有沒有給出*機制*說明為何這樣？還只是直覺？若只是直覺，論文要麼 (a) 提出一個機制並明寫它是 theoretical，要麼 (b) 放棄 junior-specific 的 claim，改 argue 較弱的「AI assistants 損害 debugging skill」版本。
>
> **根據你之前說的，我建議的答案：** 提出機制、並明寫它是 theoretical。機制如下：senior 已經持有讓 AI suggestion 套進去的 mental model，所以 AI output 會在他內部那個既有 representation 上做 verification。Junior 還未持有那個 model；AI output 沒有可以對校的 referent 就被接受了。這跟 Bainbridge 的框架（人類對 automation 接手的那部分會退化）一致，但加了一個 acquisition-stage 的轉折——automation 最傷的地方，是人類仍在建立那個被 automation 取代的 model 的時候。
>
> **為甚麼這條重要：** 沒有機制，「junior 不同」只是 hand-waving。有機制，它就變成可測試的 Bainbridge 延伸，論文也因此擁有自己的 theoretical contribution。

**使用者答案：** 這個機制正正是我想表達但講不出來的東西。就用它。

---

Q4 之後 Readiness checklist 全部過關。（五項：thesis 站得住 ✓、≥2 sub-claims ✓、個人角度 ✓、最強反論已點明 ✓、每條 sub-claim 都已說明所需證據類型 ✓。）下方為 Output block。

## Output block

```markdown
## Thesis
Generative AI coding assistants 透過取代 productive struggle，損害 junior developer 對 debugging skill 的習得；而 productive struggle 正是建立 debugging 所依賴的 mental model 的途徑——這個傷害有 acquisition-stage 的特異性，與 Bainbridge 的 ironies of automation 一致，並對它作出延伸。

## Sub-claims
1. Debugging skill 依賴 developer 對系統的 mental model；這個 model 是在 construction 階段透過 effortful engagement 建立的，不是靠 passive exposure 得來。
2. AI coding assistants 把 construction 階段的努力換成「接受 / 不接受」的 acceptance decision——productive struggle 被一個低 cognitive load 的決定取代。
3. 對 junior 的傷害比對 senior 嚴重，因為 senior 把 AI output 跟既有的 mental model 對校來 verify，而 junior 是「沒有 model 才去用 AI output」——automation 在「技能仍在習得當中」的階段最具殺傷力。

## Personal angles
- 使用者上學期幾乎完全靠 AI 寫了 side project，之後 debug 不到自己寫的程式。論文應該從這個經驗的內部寫，HCI 學科容許的話用第一人稱；不要擺成外部觀察者或道德家。
- 把機制框在 cognitive load 與 deliberate practice（課程第 3–5 週的材料）之上，不要寫成泛泛的「AI 不好」。

## Counterarguments to address
- 生產力反論：Peng et al. (2023) 顯示 Copilot 用戶完成任務快約 55%。完全接受；論證 task-completion productivity 與 skill acquisition 是兩個構念，生產力 finding 沒有量度後者。
- 「計數機類比」反論：計數機沒有摧毀數學能力，AI assistants 也不會摧毀程式能力。回應：以 cognitive load theory 作 warrant，區分 computational off-loading（計數機）與 model-construction off-loading（AI）。

## Evidence needed
- 奠基：Bainbridge (1983) ironies of automation，直接引用。
- 奠基：cognitive load theory 與 deliberate practice——Sweller (1988) 或其後續，Ericsson, Krampe, & Tesch-Römer (1993) 或其後續。
- 實證（近期）：至少一項 2022+ 的 AI coding assistants 研究。Peng et al. (2023) 用於生產力反論；對 novice 傷害的實證研究（例：Prather et al. 2024 或同等的 CHI/ICER 論文）支撐 Sub-claim 3。
- 反證實證：例：Kazemitabaar et al. (2023)——若研究可靠，作為「合適 scaffolding 下 AI 對 novice 反而有助」的反證，避免論文一面倒。

## Open questions
- 目前發表的 AI coding assistants 證據集中在 Copilot 與短時任務情境；使用者那種「多週 side project」的情境在 literature 中嚴重 undersampled。論文要老實寫出這個 limit，不可過度推論。
- Sub-claim 3 的 junior-specific 機制是 theoretical，沒有被直接測試過。論文中要明寫，作為待 empirical follow-up 的 theoretical contribution。
```

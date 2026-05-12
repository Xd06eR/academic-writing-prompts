# Essay Context（共用前置區塊）

> 這個區塊**每篇論文只需填一次**。在每次呼叫 skill 時，把它貼在最上面（`1-擷取論點`、`2-文獻回顧`、`3-大綱`、`4-起草`、`5-修訂` 都一樣）。所有 skill 都假設下列欄位已填好。

## Essay Context

- **題目與立場（Topic and stance）：** [一句話交代題目 + 你的立場。例：「社交媒體使用主要透過拖延機制，損害大學生的學業表現。」]
- **學科（Discipline）：** [例：心理學、計算機科學、文學、社會學]
- **目標讀者（Target audience）：** [例：本科同儕、課程教授、學術期刊讀者]
- **引用格式（Citation style）：** [例：APA 7、MLA 9、Chicago 17、IEEE]
- **範圍（Scope）：**
  - `full` —— 一次寫整篇；或
  - `section:<名稱>` —— 只寫某一節（例：`section:literature_review`、`section:introduction`、`section:body_paragraph_2`）
- **字數——整篇（Word count, full essay）：** [例：2000]
- **字數——負責那節（Word count, responsible section）：** [Scope 是 `section:*` 時才填，否則留空。]
- **特定要求（Specific requirements）：** [教授開出的任何條件：必用的理論框架、必引或必避的來源、格式偏好、評分項。沒有就留空。]
- **個人脈絡（Background context / your angle）：** [你的親身經驗、之前讀過的東西、課程主軸、或應該滲入文章的角度。這就是讓論文不像 generic AI output 的關鍵。]

## 給 assistant 的備註

- 把使用者（也就是學生）當作**論點的擁有者（owner of the argument）**。你的角色是結構化、潤飾、壓力測試他的想法——絕對不替他發明立場。
- 若上述欄位有空白或含糊，在動手前最多問 **3 條釐清問題**。問完 3 條仍未清楚，就用合理 default 繼續，並把這些假設明寫出來。
- 若 `Scope` 是 `section:*`，提到其他節時只能用暗示（例：「如 literature review 所建立的……」）。不要替使用者寫其他節。
- 引用守則：絕不杜撰引文。若某主張無法用有 URL/DOI 的來源支持，就刪掉該主張、或標 `[需要引用]`、或改寫成不需要那條引用。

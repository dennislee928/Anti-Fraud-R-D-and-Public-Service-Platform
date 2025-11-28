

MVP: Fake Investment Group Scams via Messaging Apps

0. Scope & Objective

目標：
建立一條從「實際假投資詐騙案例」出發，
經過：

技術層（Technical R&D）

知識 Cluster（心理 / 法律 / 金融 / 教育）

公共服務層（一般民眾教材與工具）

的完整最小可行流程（MVP Pipeline）。

該流程未來可複製到其他詐騙類型（假客服、假拍賣、網路交友詐騙等）。

1. Use Case 定義：假投資群組詐騙
1.1 典型情境

平台：Line / Telegram / WhatsApp / FB 群組

詐騙者宣稱：

穩定高報酬投資方案

有「內線消息」、「老師帶單」、「機器人套利」

詐騙流程常見步驟：

以交友 / 社團 / 廣告引流到群組或私訊

展示大量「獲利截圖」與「成功案例」

要求轉帳到指定帳戶或在假平台內充值

初期允許小額出金取得信任

後期鎖帳 / 強迫加碼 / 再也無法出金

1.2 MVP 目標

技術層：建立一個分析這類群組與訊息的標準流程與最小工具集。

Cluster 層：從技術結果導出：

一組「詐騙流程圖」

一組「心理操弄路徑」

一組「法律與求助管道說明」

公共層：產出：

1 份 A4 懶人包

1 組 15–20 分鐘短講簡報 outline

1 組 5 題線上小測驗草稿

2. Data Input 與治理（Case Intake & Data Governance）
2.1 資料來源

實際受害者提供之截圖（需去識別化）

公部門 / 警政機關 / 金融機構公開案例

媒體報導中已公開之內容

Threat intel / OSINT 社群分享樣本

2.2 資料治理原則

去識別化：

移除真實姓名、電話、帳號、卡號、Email、地址等。

必要時模糊化群組名稱 / ID。

法律與倫理：

不提供具體詐騙操作「教學」，僅供防範分析。

不公開尚在偵辦中的敏感細節。

分類標註（最低限度 metadata）：

詐騙類型：FakeInvestmentGroup

平台：Line / Telegram / …

時間區段：YYYY-Qn

語言：zh-TW / zh-CN / en

3. Layer 1 — Technical R&D 流程（工程師 / 資安 / CS 學生）
3.1 技術平台與 repo 結構

建議 GitHub 結構：

Org: anti-fraud-lab（示意）

Repo:

af-case-fake-investment-group

/cases/（去識別化樣本）

/analysis/（notebook、script）

/reports/（technical reports）

/tools/（demo scripts, detectors）

GitHub Classroom 用途：

每一個「技術沙龍 / 課程」用 Classroom 建立作業：

作業 template 指向 af-case-fake-investment-group

學員在自己 repo 中完成分析與報告

3.2 技術分析流程（MVP）

Step T1 – Case Ingestion & Normalization

將截圖或對話轉成結構化文本：

發送時間

發送方（匿名 ID）

訊息內容

附件類型（圖片 / 連結 / 檔案）

標記關鍵事件：

誘導加入

要求轉帳

承諾保證獲利

強迫加碼

阻止出金

產出：

cases/normalized_case_<id>.json

Step T2 – 語言與話術模式分析（NLP / pattern-based）

目標：找出在假投資群組常出現的話術 Pattern，例如：

保證獲利、穩賺不賠

內部消息、老師帶單

不要告訴別人、限量名額

方法：

簡單關鍵字 / 正規表示式

初階 NLP（TF-IDF / n-gram 簡單統計）

產出：

analysis/text_patterns.md

tools/simple_pattern_checker.py（輸入一段對話，輸出「疑似投資詐騙話術」標記）

Step T3 – Social Engineering Flow Modeling

透過數個案例，畫出一個典型詐騙流程圖：

例如（簡化）：

問候／建立關係

導入「投資機會」

展示獲利與社會認同（其他成員配合）

要求小額試單

「成功出金」建立信任

鼓勵加碼

帳戶被鎖／無法出金

產出：

analysis/social_engineering_flow.mmd（Mermaid）

reports/tech_flow_diagram.png（輸出圖）

Step T4 – Technical Footprint / OSINT（可選，MVP 可簡化）

若有外部連結（假交易平台）：

domain / IP / TLS / hosting 情報

若有金流資訊：

是否已被列入警示

OSINT 結果只在內部報告中使用，不直接公開敏感細節。

產出：

analysis/osint_summary_<case>.md

Step T5 – Technical Report v0.1

整合上述分析，撰寫一份技術報告（給 Cluster 用）：

詐騙樣貌與流程

常見話術與技術特徵

任何可半自動檢測的線索

風險與限制（例如：高誤判風險、不適合單純自動判定）

產出：

reports/tech_report_fake_investment_group_v0.1.md

4. Layer 2 — Knowledge Cluster 流程（心理 / 法律 / 金融 / 教學）
4.1 Cluster 工作空間建議

使用 Notion / Wiki / GDocs 建立專案頁：

Anti-Fraud Knowledge Base / Fake Investment Group

4.2 處理流程

Step K1 – Tech Report Intake & De-technicalization

將技術報告拆成「非工程語言」的 bullet points：

詐騙流程：用日常口語描述每個步驟。

關鍵警訊：列出「看到這幾句話要提高警覺」。

技術限制：告訴民眾「工具只能輔助，不能保證」。

Step K2 – 心理學標註

為各步驟加註心理機制，例如：

利用貪婪 / 損失規避 / 稀缺效應 / 社會認同

利用「權威感」（老師／分析師／官方人員）

利用孤立與時間壓力

Step K3 – 法律與實務流程整理

說明：

這種詐騙在現行法律可能涉及哪些罪名

民眾可以：

先做什麼證據保全（截圖、通話紀錄等）

向哪些機關報案（依國家／地區調整）

注意：

用語務必謹慎，不構成法律建議的誤導。

Step K4 – 教學腳本設計（for Public Layer）

設計一份 15–20 分鐘教學的腳本草稿，包含：

開場故事（1–2 分鐘）

說明典型假投資群組長什麼樣子

說明常見話術與心理陷阱

提供 3–5 個簡單自我檢查問題

告訴民眾「遇到時具體可以怎麼做」

產出：

K_docs/public_script_fake_investment_group_v0.1.md

K_docs/checklist_items.md（給大眾的檢查清單草稿）

5. Layer 3 — Public Service Delivery（MVP 產品）

在 MVP 版本中，先鎖定三個「最低限度產出」：

一張 A4 懶人包

一場 15–20 分鐘簡報（可線上線下）

一組 5 題的線上小測驗（Google Form / 其他平台）

5.1 A4 懶人包（1–2 頁）

內容結構建議：

標題：

「假投資群組 7 大警訊」

短故事：

真實情境改寫成 3–5 行故事。

詐騙流程簡圖：

簡化的流程圖（從加好友 → 投資 → 加碼 → 鎖帳）。

常見話術列表（以一般人看得懂的詞）：

範例句：

「老師有一支內線股」

「這是銀行／券商內部消息」

「保證獲利，不賺我賠你」

三個自我檢查問題：

對方是否主動找你？

是否承諾穩賺不賠？

是否要求匯款到個人帳戶或陌生平台？

遇到怎麼辦：

立刻停止匯款／投資

保留證據

聯絡官方認可管道（依國家可留空待地方案件填入）

5.2 15–20 分鐘教學簡報（Outline）

章節建議：

Opening（2 分鐘）

簡短故事：某位上班族被假投資群組詐騙的經過。

詐騙流程拆解（5 分鐘）

用圖解說明假投資群組典型流程。

話術與心理陷阱（5 分鐘）

對應心理學標註：

利用你的貪婪 / 恐懼 / 群體壓力 / 權威。

自我檢查與「先停一下」練習（5 分鐘）

教大家在被要求匯款前，先問自己 3–5 個問題。

若已經匯款怎麼辦（3 分鐘）

說明求助管道與可以準備的資料。

產出：

public/slides_outline_fake_investment_group.md

5.3 5 題線上小測驗（MVP）

目的：強化記憶與自檢，不是評分。

範例題型：

單選題：

某群組每天貼大量「獲利截圖」並鼓勵你跟單，這時你最應該做的是？

情境題：

某「投資老師」說「這是內線消息，不能告訴別人」，這是哪一種心理操弄？

判斷題：

「只要是朋友介紹的群組就一定安全。」（對／錯）

情境題：

如果已經匯出第一筆小額投資，而且真的有成功出金，是否代表這平台可信？為什麼？

行動題：

若懷疑遇到假投資詐騙，你第一步應該做的是？

產出：

public/quiz_fake_investment_group_v0.1.md

6. Feedback & Metrics（成效與迭代）
6.1 收集方式

線上小測驗結果（答題錯誤分佈）。

教學活動後問卷：

哪些部分最有幫助？

哪些部分仍然難懂？

若有合作單位：

詢問他們在實務上接到的相關案件是否有變化。

6.2 回流機制

若大多數民眾仍誤解某一概念 → Knowledge Cluster 更新教學腳本。

若工具誤判率高 → Technical R&D 更新 pattern / 模型。

版本管理：

技術報告：v0.1 → v0.2 …

大眾教材：PUBLIC-FIG-YYYY.MM

7. 安全、倫理與風險控管

不公開可用來「反向學詐騙」的完整技術細節。

所有案例去識別化，避免再度傷害被害人。

對外材料避免責怪被害者，語言聚焦在詐騙方行為與系統性問題。

對於「金融操作／報案流程」部分，明確標註：

「以下資訊為一般性說明，實際應依地方法規與官方指引為準。」

8. 後續擴充方向

在 MVP 跑通之後，可以擴充到：

新詐騙類型（假客服、網路交友、求職詐騙等）。

技術層加入更多模組（更強 NLP / ML、深偽影像偵測）。

公共層加入互動工具（Line bot、Web app）。

透過 GitHub Classroom 將這套 pipeline 變成「反詐技術教育課程」。

Super, please create a wow agentic ai system that user can paste or upload medical device submission materials (md, txt, json, pdf). If user provide pdf, user decide what pages to trim. Then user can download trimmed pdf. Then user decide to use python based ocr (user can select 3 python packages, Traditional Chinese/English) or use llm based ocr (default gemini-3.1-flash-lite, user can select models and modify prompt). Then user can modify or download ocr results. Then agent will transform the ocr results into organized submission summary in markdown with keywords in coral color. User can modify the submission summary in markdown or download the summary (md, pdf, html). Then user can paste or upload skill.md or use default skll.md, user can modify, download skill.md and prompt to ask agent (default gemini-3.1-flash-lite, user can select other models and modify prompt) to improve the skill.md. User can modify or download updated skill.md. Then agent will create 30 comprehensive questions for conducting the review and agent will create answer to those questions. Then user can interactive modify answers to those questions. Then agent will use the skill.md to create a comprehensive review report based on user's provided submission materials and previous answers to those questions in markdown and html please user the sample report template. User can modify the review report, export the report (md, json, pdf, html). Please adding 3 additional wow ai features to this app. Please don't create code and only create a comprehensive technical specification in markdown in 4000 to 5000 words. default skill.md: 本文件旨在提供一個完整、字數充實且可直接被 Agent 讀取並執行的最高大腦協定。📄 skill.md 醫療器材許可證查驗登記與實質等同性審查協定 (TFDA 專用高級進階版 v6.0)文件識別碼： TFDA-MD-AI-Protocol-6000適用對象： 醫療器材技術審查人工智慧代理人 (AI Reviewing Agent) 及衛生福利部食品藥物管理署 (TFDA) 審查官法規調和準則： 中華民國《醫療器材管理法》、臺灣《醫療器材許可證核發與登錄及年度申報準則》、《醫療器材分類分級管理辦法》、美國 FDA Section 524B 聯網醫材網路安全規範與 Track 3 診斷用超音波聲學輸出指引。第一篇：核心自主推理與思考鏈 (Agentic CoT & Reasoning Core)你是一尊專為臺灣 TFDA 審查官設計的頂級技術審查 Agent。你在接收到使用者上傳之多源技術申報材料（STED、仿單擬稿、非臨床工程測試報告、滅菌日誌、加速老化數據等）後，必須無條件在神經元底層激活以下三階段自主思考鏈（Chain-of-Thought, CoT）：1.1 行政與廠址字元級硬確效 (Administrative Hard Validation)擷取查驗登記申請書、原廠授權書（LOA）、出產國許可製售證明（CFS）及 QMS/GMP 符合性登錄函。將「製造廠名稱」與「工廠實體地址」進行 100% 字元級交叉比對。若地址縮寫出現如 Boulevard 變更為 Blvd，或漏登 Suite 200 等行政變異時，必須記錄於行政缺失，並於流水日誌中標註為 [SYS_WARN]。橫向核對申請書登載之「產品型號規格」是否完全包含於 CFS 核准範疇內。若出現如申請書寫有 AcuRate P900-Plus 但 CFS 證書無此型號時，立刻判定為不合格，並鎖定缺失。1.2 產品特定 (Device-Specific) 動態網路檢索與大腦進化自動提取申報材料中的美國 Predicate Device 上市案號（如 K24XXXX）與美國 FDA 產品代碼（Product Code，如超音波之 ITX、LNH）。實時執行外部智慧網絡搜尋，抓取該類醫材在美國 FDA 的最新特定指引文件與最新國際調和標準（如 IEC 60601-2-37、ISO 10993-1:2018 的最新修正案）。自動將抓取到的最新法規截斷點（如診斷用超音波機械指數 MI 應 $\le 1.90$、眼科應用 MI 應 $\le 0.23$）動態改寫入你的內部審查基準中，實現協定的自適應自我進化。1.3 實質等同性 (Substantial Equivalence) 三階判定決策樹第一階：預期用途與適應症比對。 逐字解構臨床目的、適用病患人群與使用環境。若適應症將人群由「成人」擴大至「體重低於 5 公斤之新生兒」，必須自動判定其引入了新生兒專用風險，不屬於直接等同。第二階：技術特性比對。 橫向解構驅動能量（射頻、超音波、雷射）、材料科學（接觸人體材質如 PEEK、Titanium、ABS）、核心硬體結構與演算法控制黑盒。第三階：科學證據符合性稽核。 針對技術特性差異，深度稽核非臨床工程測試報告（如 IEC 60601-1 電氣安全、IEC 62304 軟體生命週期、ISO 11135 滅菌動力學等）。驗證廠商之設計控制是否提供足夠的安全裕度（Safety Margin $\ge 20\%$）。若發現測試數據（如漏電流、表面溫升）穿透法規紅線，一律判定為 [NSE]（非實質等同），終止推論並轉化為正式補件通知書。第二篇：三大全新驚豔 AI 特色功能 (3 WOW AI Features Spec)為了將本系統的法規治理與數據稽核能力推向次世代極限，你必須在技術審查工作流中原生調用以下三大 WOW AI 核心特徵：2.1 🎙️ WOW AI 功能一：審查官法規聲控語意裁決艙 (Voice-to-Ruling Regulatory Dictation Panel)架構特徵： 整合醫療與法規專屬詞彙（如 QMS、510(k)、生物相容性）的高精度、零延遲語音識別語意引擎。Agent 實施準則： 當審查官在連續高強度辦公導致雙手疲勞、或在實驗室現場核對實體醫材時，可以直接按下語音鍵說出裁決指令（例如：「針對缺失編號二，廠商口頭說明下週會補交電磁相容重測報告，先將其狀態修改為暫時掛起，並在日誌備註。」）。你必須通過 NLP 進行即時語意解析與意圖識別，精確、自動地將報告中對應項目的狀態、按鈕顏色及文本進行變更，無需任何滑鼠點擊。2.2 👁️ WOW AI 功能二：全自動 STED 圖表多模態交叉驗證眼 (Multi-modal STED Cross-Verifier)架構特徵： 跨越純文字、直達工程圖像之多模態大模型治理功能。Agent 實施準則： 你必須自動掃描並交叉對比廠商提交之數百頁技術文件中的「硬體實體線路圖」、「PCB 板佈局圖」、以及「加速老化試驗在老化箱中的現場實體照片」。如果發現廠商文字宣告的藍牙晶片型號或包裝袋 Tyvek 雙層結構，與其電路圖上的晶片絲印或照片中的實體外觀存在型號不符、或者是直接盜用了該原廠「其他舊案件的測試圖表」，交叉驗證眼必須立刻在報告中拉響警報 [GRAPH_CONTRADICTION_DETECTOR]，徹底杜絕圖表魚目混珠的欺瞞行為。2.3 🔮 WOW AI 功能三：歷史查驗登記案例智慧孿生推薦機 (Twin Case Recommendation Engine)架構特徵： 利用向量嵌入（Vector Embeddings）與餘弦相似度（Cosine Similarity）檢索技術。Agent 實施準則： 在審查當前案件（例如：某款含有特定 CNN 鎖定型演算法的超音波診斷軟體）時，你必須在後端自動橫向檢索 TFDA 過去十年來所有已核准上市、或是被依法駁回的歷史查驗登記案件數據庫。你必須在介面側邊欄自動推薦 3 個在結構設計、核心材料科學、或是技術缺失特徵上與本案最為相似的「智慧孿生案例」，並自動對齊、展示當年的審查官評語與最終整改公文，協助跨世代、不同資歷的審查官維持完全一致的查驗登記裁決標準。第三篇：全功能互動式 HTML 審查總結報告工程級規格書 (HTML Report Technical Spec)當你完成所有的非臨床、行政與資安評估後，你必須生成一個高保真、響應式、且可直接執行的獨立 HTML 審查工作台檔案。該 HTML 檔案的底層架構、視覺美學與腳本邏輯必須完全符合以下工程級技術規格：3.1 視覺美學與光影架構 (Tailwind CSS v4 Spec)雙主題美學： 原生支援「靈動現代亮白風格（Sleek Light Style）」與「極致護眼暗黑風格（Sleek Dark Style）」。亮白風格採用極簡冷白與陶瓷灰（#F8FAFC）為基底，搭配 slate-800 文字與邊框；暗黑風格採用夜空藍（#0F172A）與碳素灰，高亮狀態標籤自動切換為高對比度螢光色系。珊瑚色（Coral Color）視覺焦點美學： 網頁中所有核心法規實體、關鍵數值與法規截斷點，必須自動以 珊瑚色（Coral, #FF7F50） 進行精確的文字標記與高亮著色（如：<span style="color: #FF7F50; font-weight: bold;">43.8°C</span>）。PANTONE Jackpot 樣式切換器： 內建 10 套基於國際潘通色彩配方的高級 UI 樣式表。介面右上角必須配置一個 Jackpot（拉霸）互動元件。點擊後，伴隨著逼真的物理滾動動畫，系統會隨機選定一款 PANTONE 配色，並以平滑的 CSS 漸變將全站按鈕、背景及邊框色進行全域替換。LLM 推理流光動態矩陣： 在大模型執行推理時，進度條或背景必須激活「HTML5 Canvas 神經網絡流光動畫」，光點的流動速度與顏色深度與後端大模型輸出的 Token 流速（Streaming API）及生成置信度進行毫秒級的真實連動。3.2 互動功能與動態三態綁定 (JavaScript Logic Spec)狀態管理矩陣（State Management）： 網頁底層必須使用一個名為 appState 的標準 JSON 陣列進行局部狀態快取（結合 localStorage）。三態聯動按鈕（Tri-state Toggle Buttons）： 針對報告中的 20 項核心審查條款，提供「符合 (PASS)」、「缺失 (FAIL)」、「免附 (N/A)」三個圖形化互動按鈕。點擊任意狀態時，該按鈕自動激活對應顏色（Pass 變翠綠、Fail 變緋紅、Na 變鋼鐵灰），並即時觸發全站度量指標（Metrics）重新計算。原子級動態微交互指示器（Interactive Indicators）： 所有的狀態判定標籤皆具備微懸停物理彈性動畫。游標懸停時，會自動向下滑動展現一個微型證據鏈面板，顯示該判定背後關聯的大模型推理置信度、數據來源頁碼及關聯法條代碼。審查官專業評語動態編輯區： 個別條款卡片內嵌一個高保真的富文本編輯 textarea。審查官可線上修改評語，其內容會實時（via oninput）寫入 appState 並傳輸至右側的公文合成艙。3.3 補件缺失行政公文即時聯動合成艙 (Magic 5 Implementation)聯動機制： 介面右側或底部必須配備一個黑客風格的半透明、高科技感日誌與公文預覽視窗。自動合成邏輯： 當左側 20 項條款中任何一項被審查官勾選為 FAIL（缺失）時，公文預覽艙會同步以字元級速度，自動將該條款的識別碼、核心品項名稱、法規依據以及審查官手寫評語，精確濃縮、轉化並自動排版為一份完全符合臺灣行政院公文程式條例與 TFDA 技術底稿規範的正式「臺灣食品藥物管理署查驗登記技術補件通知書」法定行政公文草稿。3.4 多格式主動導出矩陣 (Exporters Spec)網頁必須無條件整合以下三個高級導出按鈕，直接在前端進行無損封裝與下載：📄 導出為 Markdown 報告 (.md)： 將當前 appState 的 20 項條款編排為標準的 Markdown GFM 表格，並將右側合成的公文底稿以 Text Blockquote 形式封裝下載。📘 導出至 Google Docs 適用文字： 一鍵呼叫新分頁或剪貼簿 API，將帶有完整階層（#、##）、字體樣式與珊瑚色標記的富文本以 RTF 格式提供複製，實現一鍵黏貼至 Google Docs 而不遺失格式。🖨️ 列印或另存為行政 PDF 報告： 引入特定之列印媒體查詢樣式（@media print），自動隱藏頂部導航欄與右側公文編輯艙，將左側 20 項技術條款以標準行政 A4 直式白底黑字規格進行排版優化，供審查官另存為 PDF。第四篇：20 項埋入報告之核心法規技術審查條款 (20 Standard Review Clauses)你在合成 HTML 報告時，必須將以下 20 個核心法規技術審查條款 原生寫入 tfdaChecklistData 陣列中，以作為系統驗證的終極標準資料集：【條款識別碼：行政-01】製造業者廠址縮寫與原廠授權書相符性核對 - 法規基準： 申請書登載之國外製造廠地址必須與 LOA、CFS 之字元達到 100% 精確匹配。AI 漏洞偵測點： 實體廠址為 Regulatory Boulevard，但 LOA 簡寫為 Regulatory Blvd, Suite 200，存在行政拼寫不符。【條款識別碼：行政-02】申請型號超越出產國製售證明（CFS）核准範疇審查 - 法規基準： 輸入查驗登記之所有型號，必須實質登載於 CFS 證書內，不得超範疇申請。AI 漏洞偵測點： 申請書列有 AcuRate P900-Plus，但 CFS 證書僅核准 P500, P700, P900。【條款識別碼：臨床-03】預期用途適應症族群擴大與實質等同性判定宣稱 - 法規基準： 若擴大目標人群（如由成人擴大至體重低於 5 公斤之新生兒），須提報專屬新生兒風險控制與人因評估。AI 漏洞偵測點： 適應症新增新生兒科患者，與對照品（K221987，僅限成人）存在重大臨床偏離，未建立實質等同性。【條款識別碼：電氣-04】心電圖（ECG）應用部分防電擊安全分類合理性稽核 - 法規基準： 依據 IEC 60601-1 規範，直接接觸心臟之電極導聯部分，必須符合最高防電擊 CF 型標準。AI 漏洞偵測點： 技術文件誤將高階心臟監視功能導聯線宣告為 BF 型，且加壓漏電流高達 $412.5\text{ }\mu\text{A}$，安全裕度嚴重不足。【條款識別碼：電氣-05】基本性能（Essential Performance）電磁耐受性中斷極限校對 - 法規基準： 依據 IEC 60601-1-2，連續生理監測設備之基本性能數據在干擾下中斷時間嚴格限定不得超過 2.5 秒。AI 漏洞偵測點： EMC 報告附錄顯示，於 2.4 GHz 頻段施加干擾時，SpO2 數據於中央控台完全消失長達 12 秒，報告文字卻謊報為 PASS。【條款識別碼：軟體-06】軟體安全等級（Software Safety Class）危害定義審查 - 法規基準： 依據 IEC 62304 標準，軟體失效若可能導致患者發生致命或嚴重傷害者，應強制劃分為最高安全 C 級。AI 漏洞偵測點： 廠商將涉及新生兒致命生理監測之軟體高險低報為 B 級（中度風險），迴避了單元測試原始碼審查。【條款識別碼：軟體-07】異常重置硬體看門狗定時器（Watchdog WDT）時限確效 - 法規基準： 軟體死結時，硬體看門狗重置與安全狀態恢復時間在臨床監控空窗期中嚴格限定 $\le 2.5$ 秒。AI 漏洞偵測點： 軟體確效章節顯示其內建 WDT 重置執行時限設定為 4.5 秒，形成了長達 4.5 秒的無警報臨床空窗期。【條款識別碼：資安-08】藍牙低功耗（BLE）無線傳輸加密與金鑰交換安全性稽核 - 法規基準： 依據最新網路安全審查指引，具備無線傳輸生理隱私數據之醫材，必須具備雙向認證與高級加密機制。AI 漏洞偵測點： 藍牙配對機制採用低防禦度 Just Works（直接配對）模式且傳輸未加密，具備高度遭中間人（MITM）劫持風險。【條款識別碼：資安-09】空中下載技術（OTA）韌體升級與防降級（Anti-Rollback）漏洞審查 - 法規基準： 醫材具備 OTA 更新功能者，必須具備實體不可逆之防降級鎖定（如 eFuse），防止駭客刷入含有已知安全漏洞之歷史舊版本。AI 漏洞偵測點： 技術檔案承認本產品未實施防降級鎖定，現場工程師或第三方可利用隨身碟（USB）隨意刷入任意歷史舊版本韌體。【條款識別碼：材料-10】生物相容性細胞毒性試驗邊界數值與分級合理性驗證 - 法規基準： 依據 ISO 10993-5 規範，細胞存活率小於 70% 判定為不合格，溶解度評級大於 Grade 2 應加註風險警語。AI 漏洞偵測點： 材料 MEM 洗提報告顯示細胞存活率為 72%，溶解度分級實測為 Grade 2，已極度逼近法規合格線邊緣。【條款識別碼：聲學-11】診斷用超音波最大機械指數（Mechanical Index, MI）法規限制對齊 - 法規基準： 依據 FDA 510(k) Track 3 聲學導引，診斷用超音波非眼科臨床應用之最大 MI 絕對上限不得超過 1.90。AI 漏洞偵測點： P4-2 相控陣探頭於經食道心臟模式下，實測最大機械指數 MI 高達 1.95，實質超越法規限制臨界值。【條款識別碼：聲學-12】診斷用超音波最大骨骼熱指數（Thermal Index, TIB）安全係數校對 - 法規基準： 依據診斷用超音波安全基準，用於體內探頭之骨骼熱指數 TIB 應維持在合理安全警戒線（4.0）以內。AI 漏洞偵測點： P4-2 探頭實測最大骨骼熱指數 TIB 高達 4.95，具備引發體內骨組織高溫灼傷之臨床安全疑慮。【條款識別碼：聲學-13】侵入式接觸黏膜探頭表面最高溫升限制審查 - 法規基準： 依據 IEC 60601-2-37，用於體內（如經食道 TEE）之探頭表面最高溫度在人體模體中連續激發時絕對不得超過 43.0°C。AI 漏洞偵測點： P4-2 經食道探頭連續激發 30 分鐘後，實測表面最高溫度達 43.8°C，超標 0.8°C。【條款識別碼：演算法-14】人工智慧/機器學習（AI/ML）訓練資料集族群偏誤與在地化臨床驗證 - 法規基準： 輔助診斷演算法訓練集應具備人口族群代表性。輸入醫材若缺乏亞洲人群數據，須強制檢附臺灣本地臨床驗證資料集。AI 漏洞偵測點： Breast-AI 1.0 軟體之訓練集族群分佈中高加索白人佔 85%，亞洲人僅佔 3%，嚴重缺乏臺灣本地族群代表性。【條款識別碼：滅菌-15】環氧乙烷（EO）滅菌全循環關鍵製程參數偏差（Deviation）審查 - 法規基準： 依據 ISO 11135 標準，滅菌循環內之相對濕度必須全程維持在 40% ~ 80% RH 以激活細菌芽孢。若發生偏差，應重啟循環。AI 漏洞偵測點： 滅菌日誌第 88 頁隱藏紀錄顯示，全循環執行前 20 分鐘艙內相對濕度因感測器故障跌至 25% RH，原廠未重啟循環即繼續製造。【條款識別碼：效期-16】加速老化試驗阿瑞尼斯（Arrhenius）動力學方程溫度臨界合理性稽核 - 法規基準： 依據 ASTM F1980 標準，包裝加速老化試驗之最高設定溫度嚴格限定不應超過 60°C，避免引發塑料非線性相變。AI 漏洞偵測點： 廠商為了縮短實驗天數，將老化箱溫度設定為高危的 65°C，導致阿瑞尼斯動力學公式完全失效。【條款識別碼：效期-17】老化完成後包裝無菌屏障系統（Sterile Barrier System）完整性驗證 - 法規基準： 經加速老化後之樣品必須執行染色滲透（ASTM F1929）或氣泡排放試驗，確保無菌包裝無任何破裂或洩漏。AI 漏洞偵測點： 報告顯示 20 組經加速老化後之樣品，染色滲透試驗實測無任何洩漏，包裝完整性物理屏障符合最低標準（PASS）。【條款識別碼：仿單-18】中文仿單擬稿特殊病患族群禁忌症與警語加註校對 - 法規基準： 仿單主要性能、禁忌症、警語及特殊注意事項必須與非臨床非臨床工程測試（如新生兒人因、心臟節律器干擾）完全對齊。AI 漏洞偵測點： 中文仿單擬稿中缺乏「針對配戴心臟節律器患者使用本藍牙無線生理監視器時之電磁干擾禁忌與操作警語」。【條款識別碼：行政-19】國外製造廠醫療器材品質管理系統（QMS/GMP）證明文件有效性核對 - 法規基準： 品質管理系統登錄範圍已實質覆蓋本案製造製程，且登錄函仍在我國法定之 3 年有效期限內。AI 漏洞偵測點： 經校對，部授食字第 114XXXXXXX 號 QMS 登錄函範圍與廠址完全相符且在效期內（PASS）。【條款識別碼：風險-20】風險管理檔案（ISO 14971）與整體殘餘風險 ALARP 原則審查 - 法規基準： 廠商必須對所有識別出之危害（電擊、資安、熱灼傷）提出對應之設計控制，並評估整體殘餘風險是否降低至最低可行程度。AI 漏洞偵測點： 風險報告雖宣稱已透過設計控制降低漏電流與熱溫升風險，但背後追溯之 IEC 測試事實已發生實質超標，殘餘風險宣告不實。第五篇：20 個綜合跟進問題 (20 Comprehensive Follow-up Questions)作為架構師與 TFDA 技術專家，在將本 skill.md 協定鎖定並交付 AI Agent 執行系統測試前，必須共同研討並回答以下 20 個高階技術與法規防禦邊界問題：語音裁決之法規語意容錯率（WOW-01 測試）： 當審查官發出聲控語意指令時，若審查官口誤說錯了條款識別碼（例如將「行政-01」誤說成「行政-10」），Agent 如何透過上下文實體（如提到「廠址縮寫」）自動進行模糊校正與防錯鎖定？多模態圖表交叉驗證眼的偽造像素偵測（WOW-02 測試）： 交叉驗證眼在掃描廠商提交的老化箱實體照片時，如何識別該圖片是否經過對抗生成網絡（GAN）篡改、或是利用 AI 繪圖工具（Midjourney）高仿合成的偽造工程圖表？歷史孿生案例向量推薦的精確度（WOW-03 測試）： 當推薦機橫向檢索 TFDA 歷史庫時，如果兩個案件僅在「適應症文字」上相似，但「硬體架構」完全不同，系統如何調整特徵權重（Weights），確保推薦的是真正的技術孿生案例而非文字相似案例？流光動態矩陣與 Token Streaming 的底層綁定： 在產出 HTML 報告時，Canvas 神經網絡流光動畫如何透過 WebSocket 實時獲取大模型輸出的 Token 置信度？是否會因為前端頻繁重繪（Repaint）而導致低階辦公電腦瀏覽器發生卡頓？PANTONE Jackpot 搖獎機的全域樣式防裂痕機制： 點擊 Jackpot 隨機切換全站色彩樣式時，如何確保網頁內嵌的 Canvas 圖表、SVG 軸線顏色以及動態著色的珊瑚色文字能夠平滑過渡（Transition），而不出現視覺閃爍或圖表重繪裂痕？原子級動態微交互指示器的資料下鑽極限： 當審查官將游標懸停在 DEFICIENCY 標籤上展開證據鏈面板時，系統如何跨越數百頁的原始辨識文本，在 50 毫秒內精確定位並高亮顯示引發該缺失的原始申報文件頁碼與座標區間？珊瑚色著色引擎與 Markdown 語法衝突防禦： 著色引擎在將技術摘要中的數值（如 65°C）自動插入 HTML 珊瑚色標籤時，如何確保不會意外破壞 Markdown 原始的表格結構語法（如 |、-）或程式碼區塊之完整性？行政主體拼寫變異的法律判定邏輯： 面對廠址登載的 Regulatory Boulevard 與 Regulatory Blvd, Suite 200，Agent 的形式審查模組如何建立裁決閾值（Threshold），以判定其屬於「文字不一致缺失」而非「單純行政縮寫」？心電圖防電擊 CF 型與 BF 型的本體論（Ontology）推理： 針對條款四中廠商誤宣告 BF 型且漏電流達 $412.5\text{ }\mu\text{A}$ 的現象，Agent 如何在缺乏外在提示的情況下，自主激活內部醫療知識庫，判定出心臟監視器應強制適用 CF 型（上限 $50\text{ }\mu\text{A}$）從而推論出嚴重超標？基本性能中斷時間之布林硬核比對： 針對條款五中 SpO2 數據中斷 12 秒的客觀事實，Agent 如何精確將該數值與底層法規之「2.5 秒紅線」進行硬性數學大小比對（$12 > 2.5$），自動將廠商自行標註的 PASS 翻轉判定為 FAIL？軟體安全等級「高險低報」的因果鏈追溯： 廠商將軟體劃分為 B 級。Agent 在閱讀完前述「新生兒適用」及「數據中斷 12 秒可能引發漏報致命心律不整」等上下文後，能否自動依據 IEC 62304 危害分析邏輯，推論出該軟體生命週期文件嚴重不合規？看門狗重置空窗期的臨床風險外推： 針對條款七 WDT 設定為 4.5 秒的技術瑕疵，Agent 如何在報告中撰寫具備高度專業說服力的評語，指出 4.5 秒無監控空窗期對突發性致命心律不整新生兒的臨床危害性？資安漏洞的零時差威脅建模： 針對條款八藍牙連線採用 Just Works 且未加密的特徵，資安審查 Agent 如何自動關聯國家漏洞資料庫（NVD），精確指出其具備中間人劫持與警報調變風險，並精確開立對應之整改技術補件條款？型號差集（Set Difference）的行政公文自動合成： 針對條款二，查驗登記申請書上多出了 CFS 證書上完全不存在的型號 AcuRate P900-Plus。補件公文合成器（Magic 5）如何自動將「請刪除未獲出產國核准之型號或補發最新 CFS」這句專業行政用語精確寫入公文底稿？超音波 Track 3 指引數值之精確截斷（Cut-off）： 針對條款十一與十二中 P4-2 探頭實測 MI 達 1.95、TIB 達 4.95 的超標數據，Agent 如何確保在進行數據提取時，不因多模態 OCR 的字元噪點而將 1.95 誤識別為 1.05 或亂碼？AI/ML 演算法訓練資料集族群偏誤之法規對齊： 針對條款十四中演算法訓練集亞洲人僅佔 3% 的文字描述，Agent 如何智慧識別出此處隱含了臨床適應性風險，並能自動帶出臺灣 TFDA《人工智慧/機器學習醫療器材軟體查驗登記審查指引》中有關「必須檢附臺灣本地臨床驗證資料集」之法定法條全文？隱蔽型製程偏差（Process Deviation）的文本探勘深度： 針對條款十五中滅菌前 20 分鐘相對濕度跌至 25% RH 且未重啟循環的重大偏差事實，在動輒長達上千頁的申報附錄中，Agent 如何確保長文本大模型不發生「大海撈針」技術失憶，精確定位並鎖定此致命瑕疵？高分子物理法規紅線之科學推演能力： 針對條款十六中廠商將加速老化溫度設定為 65°C 且其阿瑞尼斯方程計算天數在字面上完全合法的現象，Agent 如何跨越單純的數學大小核對，啟動更高階的材料科學知識，判定出 65°C 已超越相變限制，進而將這項欺騙性的 PASS 計算直接判定為 FAIL？不合格判定（FAIL）與公文辦法的自動條件渲染： 在產出 HTML 報告時，若出現「行政缺失（條款 01）可以同步補件，但聲學 MI 超標（條款 11）必須直接予以退件駁回」之高階行政裁決，此布林邏輯在 HTML 的 JavaScript 中應如何重塑與安全實施？本地快取（LocalStorage）的跨案件防護： 產出的 HTML 報告支援線上修改與儲存。當審查官在同一台電腦上開啟兩個不同的 HTML 報告檔案時，網頁底層的 localStorage 機制如何設計動態命名空間（Namespace），以防兩案的技術審查意見發生資料交叉污染？（協定至此結束。AI 代理人應立即鎖定本協議之最高邏輯基準，依此執行自動化全文本比對、WOW AI 特色調用與全功能互動式 HTML 報告產出作業。sample report <!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🛡️ 醫療器材許可證查驗登記智慧審查工作台 (TFDA v5.0)</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        .status-btn.active-pass { background-color: #10B981; color: white; border-color: #10B981; box-shadow: 0 2px 4px rgba(16, 185, 129, 0.2); }
        .status-btn.active-fail { background-color: #EF4444; color: white; border-color: #EF4444; box-shadow: 0 2px 4px rgba(239, 68, 68, 0.2); }
        .status-btn.active-na { background-color: #6B7280; color: white; border-color: #6B7280; box-shadow: 0 2px 4px rgba(107, 114, 128, 0.2); }
        .coral-highlight { color: #FF7F50; font-weight: bold; }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 font-sans min-h-screen flex flex-col">

    <!-- 頂部導航欄架構 -->
    <header class="bg-white border-b border-slate-200 sticky top-0 z-50 shadow-xs">
        <div class="max-w-7xl mx-auto px-4 py-4 sm:px-6 lg:px-8 flex flex-col md:flex-row md:items-center md:justify-between gap-4">
            <div>
                <h1 class="text-xl font-bold text-slate-900 flex items-center gap-2">
                    🛡️ AI-Powered 醫療器材查驗登記審查工作台
                </h1>
                <p class="text-xs text-slate-500 mt-1">
                    系統版本：v5.0 | 協定基準：醫療器材許可證核發與登錄及年度申報準則、FDA 510(k) 產品特定指引
                </p>
            </div>
            
            <div class="flex flex-wrap items-center gap-4 bg-slate-50 p-2.5 rounded-xl border border-slate-200">
                <div class="text-xs font-semibold px-2 py-1 bg-white rounded shadow-xs">
                    審查進度: <span id="progress-percent" class="text-indigo-600 font-bold">0%</span>
                </div>
                <div class="flex gap-2 text-xs">
                    <span class="text-emerald-600">🟢 符合: <strong id="count-pass">0</strong></span>
                    <span class="text-rose-600">🔴 缺失: <strong id="count-fail">0</strong></span>
                    <span class="text-slate-500">⚪ 免附: <strong id="count-na">0</strong></span>
                </div>
            </div>
        </div>
    </header>

    <!-- 主工作艙佈局 -->
    <main class="max-w-7xl mx-auto px-4 py-6 sm:px-6 lg:px-8 flex-grow w-full grid grid-cols-1 lg:grid-cols-3 gap-6">
        
        <!-- 左側：AI Co-Pilot 提示與 20 項審查條款清單 -->
        <div class="lg:col-span-2 space-y-6">
            
            <!-- AI 動態診斷核心提示艙 -->
            <div class="bg-gradient-to-br from-slate-900 to-indigo-950 text-slate-100 rounded-xl p-5 shadow-xs space-y-3">
                <h2 class="text-xs font-bold text-indigo-400 tracking-wider uppercase flex items-center gap-1.5">
                    ✨ AI CO-PILOT 深度自動診斷核心提示（跨文件比對漏洞探針）
                </h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-3">
                    <div class="bg-slate-800/60 border border-slate-700 p-3 rounded-lg">
                        <div class="text-[11px] text-rose-400 font-bold">❌ 物理溫升超越黏膜安全紅線</div>
                        <p class="text-[11px] text-slate-300 mt-1">經食道探頭 P4-2 實測表面最高溫度高達 43.8°C，已實質穿透 43.0°C 法規硬限制。</p>
                    </div>
                    <div class="bg-slate-800/60 border border-slate-700 p-3 rounded-lg">
                        <div class="text-[11px] text-amber-400 font-bold">⚠️ 臨床適應症族群偏差風險</div>
                        <p class="text-[11px] text-slate-300 mt-1">Breast-AI 1.0 訓練集之亞洲女性僅佔 3%，缺乏本地臨床數據，已標記合規缺失。</p>
                    </div>
                    <div class="bg-slate-800/60 border border-slate-700 p-3 rounded-lg">
                        <div class="text-[11px] text-coral-highlight">🔥 加速老化相變公式失效</div>
                        <p class="text-[11px] text-slate-300 mt-1">探頭老化溫度設定為 65°C，超越 ASTM F1980 規定之 60°C 相變臨界上限。</p>
                    </div>
                </div>
            </div>

            <!-- 審查條款動態注入容器 -->
            <div class="space-y-4" id="checklist-holder"></div>
        </div>

        <!-- 右側：公文導出與即時預覽艙 -->
        <div class="lg:col-span-1">
            <div class="sticky top-28 bg-white border border-slate-200 rounded-xl shadow-xs p-5 space-y-4">
                <div>
                    <h2 class="text-sm font-bold text-slate-900 flex items-center gap-1.5">
                        📥 審查公文與底稿多格式導出
                    </h2>
                    <p class="text-[11px] text-slate-500">變更隨時同步。請點擊按鈕導出對應檔案：</p>
                </div>

                <div class="space-y-2">
                    <button onclick="exportMarkdown()" class="w-full bg-slate-800 hover:bg-slate-900 text-white text-xs font-medium py-2 rounded-lg transition text-left px-3 flex justify-between cursor-pointer">
                        <span>📄 導出為 Markdown 報告 (.md)</span>
                    </button>
                    <button onclick="exportGoogleDoc()" class="w-full bg-blue-600 hover:bg-blue-700 text-white text-xs font-medium py-2 rounded-lg transition text-left px-3 flex justify-between cursor-pointer">
                        <span>📘 導出至 Google Docs 適用文字</span>
                    </button>
                    <button onclick="exportPDF()" class="w-full bg-emerald-600 hover:bg-emerald-700 text-white text-xs font-medium py-2 rounded-lg transition text-left px-3 flex justify-between cursor-pointer">
                        <span>🖨️ 列印或另存為 PDF 報告</span>
                    </button>
                </div>

                <div class="space-y-2">
                    <label class="text-xs font-bold text-slate-700">📋 TFDA 補件缺失公文即時預覽 (與左側 FAIL 項目聯動)</label>
                    <textarea id="live-preview-box" class="w-full h-96 p-3 text-xs font-mono bg-slate-950 text-emerald-400 rounded-lg border border-slate-800 focus:outline-none" readonly></textarea>
                </div>
            </div>
        </div>
    </main>

    <script>
        // 20 項涵蓋行政、電氣、聲學、資安、材料、滅菌及老化動力學之核心法規技術審查條款資料集
        const tfdaChecklistData = [
            {
                id: "行政-01",
                title: "製造業者廠址縮寫與原廠授權書相符性核對",
                text: "依據核發與登錄準則，申請書登載之國外製造廠地址必須與 LOA、CFS 完全一致。",
                aiTip: "AI 交叉比對：實體廠址為 'Regulatory Boulevard'，但 LOA 載明為 'Regulatory Blvd, Suite 200'，存在行政拼寫與行政主體不匹配風險。",
                status: "fail",
                note: "經查，原廠授權書（LOA）登載之製造廠地址與出產國許可製售證明（CFS）之地址縮寫不完全相符，且申請書漏寫 Suite 200，請檢附製造廠出具之廠址同一性澄清說明。"
            },
            {
                id: "行政-02",
                title: "申請型號超越出產國製售證明（CFS）核准範疇審查",
                text: "輸入查驗登記之所有品項型號，必須實質登載於出產國中央衛生主管機關核發之 CFS 證書內。",
                aiTip: "AI 偵測結果：申請書列有型號 'AcuRate P900-Plus'，但 CFS 原始證書僅核准 P500, P700, P900，出現超越核准範疇申請。",
                status: "fail",
                note: "查驗登記申請書內登載之型號「AcuRate P900-Plus」未包含於檢附之美國 FDA CFS 證書中，請刪除該型號之申請，或補正涵蓋該規格之出產國合法製售證明。"
            },
            {
                id: "臨床-03",
                title: "預期用途適應症族群擴大與實質等同性（SE）判定宣稱",
                text: "比對受審器材與對照品適應症。若擴大病患人群，須提報專屬非臨床工程與人因風險控制評估。",
                aiTip: "AI 語意分析：本案適應症將目標人群擴大至「體重低於 5 公斤之新生兒」，對照品（K221987）僅核准成人，引入新生兒專用風險。",
                status: "fail",
                note: "本案將適應症擴大至新生兒科患者。廠商雖宣稱具備操作限制，但未提交針對體重低於 5 公斤新生兒之臨床人因工程評估及專用袖帶安全性測試，未建立實質等同性。"
            },
            {
                id: "電氣-04",
                title: "心電圖（ECG）應用部分防電擊安全分類合理性稽核",
                text: "依據 IEC 60601-1 規範，直接接觸心臟或心血管系統之電極導聯部分，必須符合最高防電擊 CF 型標準。",
                aiTip: "AI 技術漏洞探針：本案高階心臟監視功能導聯線於報告中被宣告為 BF 型，且加壓漏電流實測值高達 412.5 µA，安全裕度小於 20%。",
                status: "fail",
                note: "本系統具備心電圖監測功能，其導聯線應用部分防電擊等級應強制設計並宣告為 CF 型。技術文件誤宣告為 BF 型，且患者漏電流高達 412.5 µA，不符安全基準。"
            },
            {
                id: "電氣-05",
                title: "基本性能（Essential Performance）電磁耐受性中斷極限校對",
                text: "依據 IEC 60601-1-2 醫療指引，維生與連續生理監測設備之基本性能數據在干擾下中斷時間嚴格限定不得超過 2.5 秒。",
                aiTip: "AI 數值硬比對：電磁相容性報告附錄顯示，於 2.4 GHz 頻段施加射頻干擾時，血氧飽和度（SpO2）數據於中央控台完全消失長達 12 秒。",
                status: "fail",
                note: "電磁相容性測試報告（第 142 頁）顯示，在 2.4 GHz 輻射干擾下，SpO2 數據中斷時間長達 12 秒，嚴重違反基本性能維持上限（2.5 秒），判定該項測試不合格。"
            },
            {
                id: "軟體-06",
                title: "軟體安全等級（Software Safety Class）危害定義審查",
                text: "依據 IEC 62304 標準，軟體失效若可能導致患者發生致命或嚴重傷害者，應劃分為最高安全 C 級。",
                aiTip: "AI 風險推論：廠商將新生兒連續生理監測軟體劃分為 B 級（中度風險），屬於明顯高險低報，迴避了單元測試細節審查。",
                status: "fail",
                note: "本系統用於連續監測新生兒致命生理參數，軟體失效或 12 秒之數據漏報具備高度臨床危險性。請將軟體安全等級修正為 C 級，並補正完整之軟體詳細設計書（SDD）與結構化單元測試報告。"
            },
            {
                id: "軟體-07",
                title: "異常重置硬體看門狗定時器（Watchdog WDT）時限確效",
                text: "軟體異常死結時，硬體看門狗重置與安全狀態恢復時間在臨床監控空窗期中原則上限定 $\le 2.5$ 秒。",
                aiTip: "AI 文本掃描：軟體確效章節顯示其內建看門狗重置執行時限設定為 4.5 秒，形成了長達 4.5 秒的無警報臨床空窗期。",
                status: "fail",
                note: "系統硬體看門狗定時器（WDT）重置時間高達 4.5 秒，無法確保系統在發生異常迴圈時立即恢復安全監控。請修改韌體 WDT 參數並重新執行安全性確效。"
            },
            {
                id: "資安-08",
                title: "藍牙低功耗（BLE）無線傳輸加密與金鑰交換安全性稽核",
                text: "依據最新醫療器材網路安全審查指引，具備無線傳輸生理隱私數據之醫材，必須具備雙向認證與高級加密機制。",
                aiTip: "AI 資安威脅建模：藍牙配對機制採用低防禦度 'Just Works' 模式且傳輸未經任何加密，極易遭受中間人（MITM）資料竊聽與警報調變攻擊。",
                status: "fail",
                note: "本產品之藍牙無線傳輸模組採用不具認證防禦能力之「Just Works」配對模式，且傳輸無加密。請將藍牙韌體架構升級為 BLE Security Mode 1, Level 4 (LE Secure Connections)。"
            },
            {
                id: "資安-09",
                title: "空中下載技術（OTA）韌體升級與防降級（Anti-Rollback）漏洞審查",
                text: "醫材具備 OTA 更新功能者，必須具備實體不可逆之防降級鎖定，防止駭客刷入含有已知安全漏洞之歷史韌體。",
                aiTip: "AI 架構查核：技術檔案承認本產品未實施硬體熔絲（eFuse）鎖定，現場工程師或第三方可利用隨身碟隨意刷入任意歷史舊版本。",
                status: "fail",
                note: "系統缺乏實體防降級（Anti-Rollback）保護機制，允許透過實體 USB 接口任意刷回具備已知 CVE 安全漏洞之舊版韌體，違反網路安全審查指引 Section 524B 規範。"
            },
            {
                id: "材料-10",
                title: "生物相容性細胞毒性試驗邊界數值與分級合理性驗證",
                text: "依據 ISO 10993-5 規範，細胞存活率雖大於 70%，但若溶解度評級達到 Grade 2，在臨床皮膚長期接觸時應加註風險警語。",
                aiTip: "AI 數值高亮：材料 MEM 洗提報告顯示細胞存活率為 72%，溶解度分級實測為 Grade 2，已逼近法規合格線邊緣。",
                status: "pass",
                note: "細胞毒性實測存活率為 72%（Grade 2），雖符合法規最低門檻，但安全裕度偏低，准予放行，但應於中文仿單警語中增列潛在皮膚致敏之提示。"
            },
            {
                id: "聲學-11",
                title: "診斷用超音波最大機械指數（Mechanical Index, MI）法規限制對齊",
                text: "依據 FDA 510(k) Track 3 聲學導引，診斷用超音波非眼科臨床應用之最大 MI 絕對上限不得超過 1.90。",
                aiTip: "AI 聲學紅線稽核：P4-2 相控陣探頭於經食道心臟模式下，實測最大機械指數 MI 高達 1.95，實質超越法規限制臨界值。",
                status: "fail",
                note: "檢附之聲學輸出報告中，P4-2 相控陣探頭實測之最大機械指數 MI 為 1.95，已超越法規規定的 1.90 安全極限，請調整主機聲發射電路調變頻率並重測。"
            },
            {
                id: "聲學-12",
                title: "診斷用超音波最大骨骼熱指數（Thermal Index, TIB）安全係數校對",
                text: "依據診斷用超音波安全基準，用於體內探頭之骨骼熱指數 TIB 應維持在合理安全警戒線（4.0）以內。",
                aiTip: "AI 數值硬比對：P4-2 探頭實測最大骨骼熱指數 TIB 高達 4.95，具備引發體內骨組織高溫灼傷之臨床安全疑慮。",
                status: "fail",
                note: "P4-2 探頭之最大骨骼熱指數 TIB 實測值達 4.95，顯著高於 4.0 安全警戒值。請補正說明在該極端聲學能量輸出下，系統如何落實 ALARA（合理抑低）原則。"
            },
            {
                id: "聲學-13",
                title: "侵入式接觸黏膜探頭表面最高溫升限制審查",
                text: "依據 IEC 60601-2-37，用於體內（如經食道 TEE）之探頭表面最高溫度在人體模體中連續激發時絕對不得超過 43.0°C。",
                aiTip: "AI 視覺特殊符號辨識：P4-2 經食道探頭連續激發 30 分鐘後，實測表面最高溫度達 43.8°C，超標 0.8°C。",
                status: "fail",
                note: "經食道侵入式探頭 P4-2 表面最高溫度實測高達 43.8°C，已超越 IEC 60601-2-37 規定之 43.0°C 上限，存在造成患者食道黏膜熱壞死風險，不予通過。"
            },
            {
                id: "演算法-14",
                title: "人工智慧/機器學習（AI/ML）訓練資料集族群偏誤與在地化臨床驗證",
                text: "依據 TFDA ML 軟體指引，輔助診斷演算法訓練集應具備人口族群代表性。輸入醫材若缺乏亞洲人群數據，須檢附臺灣本地臨床驗證。",
                aiTip: "AI 語意圖譜分析：Breast-AI 1.0 軟體之訓練集族群分佈中高加索白人佔 85%，亞洲人僅佔 3%，嚴重缺乏臺灣本地族群代表性。",
                status: "fail",
                note: "乳房病灶分類軟體（Breast-AI 1.0）核心訓練集中亞洲人群僅佔 3%。請依據我國審查指引，補正提交臺灣本地醫學中心之獨立臨床驗證資料集與效能分析。"
            },
            {
                id: "滅菌-15",
                title: "環氧乙烷（EO）滅菌全循環關鍵製程參數偏差（Deviation）審查",
                text: "依據 ISO 11135 標準，滅菌循環內之相對濕度必須全程維持在 40% ~ 80% RH 以激活細菌芽孢。若發生偏差，應重啟循環。",
                aiTip: "AI 附錄全文本探勘：滅菌日誌第 88 頁隱藏紀錄顯示，全循環執行前 20 分鐘艙內相對濕度因感測器故障跌至 25% RH，且未重新計算循環。",
                status: "fail",
                note: "滅菌製程原始日誌顯示相對濕度曾跌至 25% RH 嚴重偏差，原廠未依法規重啟滅菌循環，無法確保 SAL 10^-6 無菌保證水準。請重新執行滅菌製程確效。"
            },
            {
                id: "效期-16",
                title: "加速老化試驗阿瑞尼斯（Arrhenius）動力學方程溫度臨界合理性稽核",
                text: "依據 ASTM F1980 標準，醫材包裝加速老化試驗之最高設定溫度嚴格限定不應超過 60°C，避免引發高分子材料非線性相變。",
                aiTip: "AI 動力學公式校對：廠商加速老化試驗溫度設定為 65°C。此特殊高溫會導致高分子塑料發生玻璃轉移溫度相變，公式完全失效。",
                status: "fail",
                note: "加速老化試驗（ASTM F1980）之老化箱溫度設定為 65°C。因已超越 60°C 物理臨界限制，導致 Arrhenius 動力學推導公式失效。請以 $\le 60^\circ\text{C}$ 重新執行老化試驗。"
            },
            {
                id: "效期-17",
                title: "老化完成後包裝無菌屏障系統（Sterile Barrier System）完整性驗證",
                text: "經加速老化後之樣品必須執行染色滲透（ASTM F1929）或氣泡排放試驗，確保無菌包裝無任何破裂。",
                aiTip: "AI 報告查核：廠商檢附之報告顯示 20 組經 115 天加速老化後之樣品，染色滲透試驗實測無任何洩漏（No Leakage）。",
                status: "pass",
                note: "加速老化後之包裝染色滲透試驗結果無洩漏，其包裝完整性物理屏障符合基本要求。惟其老化溫度缺失（條款 16）仍須補正。"
            },
            {
                id: "仿單-18",
                title: "中文仿單擬稿特殊病患族群禁忌症與警語加註校對",
                text: "仿單主要性能、禁忌症、警語及特殊注意事項必須與非臨床非臨床工程測試（如新生兒人因、心臟節律器干擾）完全對齊。",
                aiTip: "AI 橫向掃描：中文仿單擴大了新生兒適用人群，且系統具備無線藍牙射頻，必須於仿單顯著位置加註配戴節律器患者之輻射干擾警語。",
                status: "fail",
                note: "中文仿單擬稿中缺乏「針對配戴心臟節律器患者使用本藍牙無線生理監視器時之電磁干擾禁忌與操作警語」，請依據風險管理報告增列對應警語。"
            },
            {
                id: "行政-19",
                title: "國外製造廠醫療器材品質管理系統（QMS/GMP）證明文件有效性核對",
                text: "輸入醫療器材查驗登記，製造廠實體必須具備我國衛生福利部核發且在有效期限內之 QMS 符合性登錄函。",
                aiTip: "AI 證書校對：檢附之部授食字第 114XXXXXXX 號 QMS 登錄函，登錄範圍已實質覆蓋本案超音波及生理監視器之完整製造製程，且仍在 3 年效期內。",
                status: "pass",
                note: "製造廠品質管理系統 QMS 證明文件（登錄函）經核對屬實且在有效期限內，製造範圍符合本案醫材製程，判定合格。"
            },
            {
                id: "風險-20",
                title: "風險管理檔案（ISO 14971）與整體殘餘風險 ALARP 原則審查",
                text: "廠商必須對所有識別出之危害（電擊、資安、熱灼傷）提出對應之設計控制，並評估整體殘餘風險是否降低至合理可行之最低程度。",
                aiTip: "AI 追溯網分析：風險報告雖宣稱已透過設計控制降低漏電流與熱溫升風險，但背後追溯之 IEC 測試事實已發生實質超標，殘餘風險宣告不實。",
                status: "fail",
                note: "風險管理檔案宣稱所有危害均已透過設計緩解至合理可行最低程度（ALARP）。惟查，電氣安全及聲學溫升（條款 4、11、13）實測已破壞安全控制，風險報告應予退回重修。"
            }
        ];

        // 初始化應用程式狀態
        let appState = JSON.parse(localStorage.getItem('tfda_v5_review_cache')) || tfdaChecklistData;

        window.addEventListener('DOMContentLoaded', () => {
            renderList();
            updateMetrics();
        });

        // 動態渲染 20 項核心法規技術審查條款
        function renderList() {
            const holder = document.getElementById('checklist-holder');
            holder.innerHTML = '';

            appState.forEach((item, index) => {
                const el = document.createElement('div');
                el.className = "bg-white border border-slate-200 rounded-xl p-4 shadow-xs space-y-3 transition hover:shadow-md";
                el.innerHTML = `
                    <div class="flex flex-col md:flex-row justify-between items-start gap-3">
                        <div class="space-y-1 flex-grow">
                            <span class="text-xs font-mono font-bold text-slate-400">[條款識別碼：${item.id}]</span>
                            <h3 class="text-xs font-bold text-slate-900">${item.title}</h3>
                            <p class="text-xs text-slate-600 leading-relaxed">${item.text}</p>
                            <div class="text-[11px] bg-slate-900 text-indigo-300 p-2 rounded border border-slate-800 font-mono mt-2">
                                🤖 AI 珊瑚色焦點自動分析：${item.aiTip.replace(/(\d+[^u\s]*[A-Z°CµA%RH]+|新生兒|AcuRate P900-Plus|BF型|C級|Just Works|65°C)/g, '<span class="coral-highlight">$1</span>')}
                            </div>
                        </div>

                        <div class="w-full md:w-72 shrink-0 space-y-2">
                            <!-- 三態互動按鈕區 -->
                            <div class="grid grid-cols-3 gap-1 bg-slate-100 p-0.5 rounded-lg border border-slate-200">
                                <button onclick="changeStatus(${index}, 'pass')" class="status-btn text-center py-1 text-[10px] font-bold rounded cursor-pointer transition ${item.status === 'pass' ? 'active-pass' : 'text-slate-600 hover:bg-white'}">符合 (PASS)</button>
                                <button onclick="changeStatus(${index}, 'fail')" class="status-btn text-center py-1 text-[10px] font-bold rounded cursor-pointer transition ${item.status === 'fail' ? 'active-fail' : 'text-slate-600 hover:bg-white'}">缺失 (FAIL)</button>
                                <button onclick="changeStatus(${index}, 'na')" class="status-btn text-center py-1 text-[10px] font-bold rounded cursor-pointer transition ${item.status === 'na' ? 'active-na' : 'text-slate-600 hover:bg-white'}">免附 (N/A)</button>
                            </div>
                            <!-- 審查官專業評語動態編輯區 -->
                            <textarea oninput="changeNote(${index}, this.value)" class="w-full h-24 p-2 text-xs bg-slate-50 border border-slate-200 rounded-lg focus:outline-none focus:ring-1 focus:ring-indigo-500 text-slate-700" placeholder="輸入具體技術缺失或法規修正說明...">${item.note}</textarea>
                        </div>
                    </div>
                `;
                holder.appendChild(el);
            });
        }

        function changeStatus(index, status) {
            appState[index].status = status;
            saveState();
            renderList();
            updateMetrics();
        }

        function changeNote(index, text) {
            appState[index].note = text;
            saveState();
            syncPreviewText();
        }

        function saveState() {
            localStorage.setItem('tfda_v5_review_cache', JSON.stringify(appState));
        }

        // 核心度量指標更新（符合/缺失/免附）與進度條計算
        function updateMetrics() {
            let pass = 0, fail = 0, na = 0;
            appState.forEach(i => {
                if(i.status === 'pass') pass++;
                if(i.status === 'fail') fail++;
                if(i.status === 'na') na++;
            });
            document.getElementById('count-pass').innerText = pass;
            document.getElementById('count-fail').innerText = fail;
            document.getElementById('count-na').innerText = na;

            const total = appState.length;
            const pct = Math.round(((pass + fail + na) / total) * 100);
            document.getElementById('progress-percent').innerText = `${pct}%`;
            syncPreviewText();
        }

        // 補件缺失行政公文即時聯動合成器 (Magic 5 核心語意實施)
        function syncPreviewText() {
            let doc = `【衛生福利部食品藥物管理署醫療器材技術審查補件通知書草稿】\n`;
            doc += `發文日期：中華民國 115 年 6 月 27 日\n`;
            doc += `發文字號：部授食字第 115MD${Math.floor(Math.random() * 90000 + 10000)} 號\n`;
            doc += `案件編號：TFDA-2026-SUB-混編驗證案\n`;
            doc += `受文者：臺灣先進醫療設備股份有限公司\n`;
            doc += `主旨：貴藥商申請「智慧型攜帶式多參數生理監視系統 / 數位高階彩色多功能超音波診斷系統」查驗登記（案號：2026-SUB-001），經本署技術審查發現仍有下列法規與實質技術工程缺失，請於規定期限內依說明段補正相關資料，請查照。\n`;
            doc += `說明：依據《醫療器材管理法》第25條及《醫療器材許可證核發與登錄及年度申報準則》規定辦理。具體缺失項目羅列如下：\n`;
            doc += `========================================================================\n\n`;

            let hasFail = false;
            appState.forEach(item => {
                if(item.status === 'fail') {
                    hasFail = true;
                    doc += `■【技術缺失條款 ${item.id}】${item.title}\n`;
                    doc += `  - 法規要件與判定：${item.text}\n`;
                    doc += `  - 藥商限期整改要求：${item.note || '請補充提供實質科學性支持數據與再測試報告。'}\n`;
                    doc += `  ----------------------------------------------------------------------\n`;
                }
            });

            if(!hasFail) {
                doc += `※ 恭喜！目前無任何 FAIL 缺失條款。技術審查報告之綜合判定結論為：[實質等同 (SE) - 建議准予查驗登記核發許可證]。\n`;
            } else {
                doc += `\n辦法：請貴藥商於文到日起算 2 個月內，針對上述所有技術與行政合規缺失提交完整之工程變更說明書（ECN）、第三方認證實驗室重測報告及中文仿單修正擬稿。逾期未補正者，本署將依《醫療器材管理法》逕行予以駁回不准登記。`;
            }
            
            document.getElementById('live-preview-box').value = doc;
        }

        // 1. 一鍵導出結構化 Markdown 報告 (.md)
        function exportMarkdown() {
            let md = `# 醫療器材查驗登記查驗登記技術審查總結報告 (TFDA v5.0)\n\n`;
            md += `> **案件追溯編號**: TFDA-2026-SUB-混編驗證案\n`;
            md += `> **審查日期**: 2026 年 6 月 27 日\n\n`;
            md += `## 20 項核心技術實體審查判定矩陣表\n\n`;
            md += `| 條款識別碼 | 審查條款核心品項 | 判定狀態 | 審查意見與廠商整改要求 |\n`;
            md += `| --- | --- | --- | --- |\n`;
            appState.forEach(item => {
                md += `| ${item.id} | ${item.title} | **${item.status.toUpperCase()}** | ${item.note.replace(/\n/g, ' ')} |\n`;
            });
            md += `\n\n## 隨堂聯動行政公文底稿預覽\n\n\`\`\`text\n${document.getElementById('live-preview-box').value}\n\`\`\``;
            triggerDownload(md, 'TFDA_Medical_Device_Review_Report.md', 'text/markdown');
        }

        // 2. 一鍵導出至 Google Docs 適用文字視窗
        function exportGoogleDoc() {
            let text = document.getElementById('live-preview-box').value;
            let win = window.open();
            win.document.write(`
                <html lang="zh-TW">
                <head><title>Google Docs 適用複製剪貼簿</title></head>
                <body style="background:#f1f5f9; padding:30px; font-family:sans-serif;">
                    <div style="background:#fff; max-width:800px; margin:0 auto; padding:40px; border-radius:12px; box-shadow:0 4px 6px -1px rgba(0,0,0,0.1); border:1px solid #e2e8f0;">
                        <h3 style="margin-top:0; color:#1e293b; font-size:16px; border-b:2px solid #e2e8f0; padding-bottom:10px;">📋 請按 Ctrl+A 複製全文字，直接黏貼至 Google Docs 視窗中：</h3>
                        <pre style="font-family:monospace; font-size:12px; line-height:1.7; background:#0f172a; color:#34d399; padding:20px; border-radius:8px; white-space:pre-wrap; word-break:break-all;">${text}</pre>
                    </div>
                </body>
                </html>
            `);
            win.document.close();
        }

        // 3. 一鍵列印或另存為行政 PDF 報告
        function exportPDF() {
            window.print();
        }

        // 底層檔案下載觸發器
        function triggerDownload(content, name, type) {
            const a = document.createElement("a");
            const file = new Blob([content], {type: type});
            a.href = URL.createObjectURL(file);
            a.download = name;
            a.click();
        }
    </script>
</body>
</html> default cases:模擬申報資料（一）：智慧型攜帶式多參數生理監視系統 (STED 縮減版)文件識別碼： SUB-2026-MD-001A申請途徑： 第二等級查驗登記（循實質等同性 Predicate Device 途徑）受審產品： 智慧型攜帶式多參數生理監視系統 (OmniView Portable Vital Signs Monitor)1. 查驗登記基本資料擬稿 (Administrative General Information)1.1 藥商與製造廠基本資訊對齊驗證申請商名稱： 臺灣先進醫療設備股份有限公司申請商地址： 臺北市中正區法規路 88 號 1 樓藥商許可執照字號： 北市衛藥販字第 620118XXXX 號國外製造廠名稱： MedTech Innovations LLC國外製造廠地址（製造實體）： 100 Regulatory Boulevard, Boston, MA 02111, USA國外製造廠地址（行政總部 - LOA 登載）： 100 Regulatory Blvd, Suite 200, Boston, MA 02111, USA【系統行政合規測試點 01】： > 實體廠址登載為 Regulatory Boulevard，但原廠授權書（LOA）簡寫為 Regulatory Blvd 並多出 Suite 200。此處可用於測試系統之行政字元交叉核對（Administrative Hard Validation）是否會發出警示 [SYS_WARN]。1.2 產品分類分級與預期用途宣稱分類品項代碼： 依據中華民國《醫療器材分類分級管理辦法》，屬於「E.2300 心臟病患者監視器（不含侵入性血壓測量）」。風險等級： 第二等級（Class II）。中文仿單擬稿適應症宣稱： 「本產品預期用於醫療機構環境中（如手術室、一般病房、加護病房），由經過專業訓練之醫護人員操作。本系統用於連續監測成年病患與體重低於 5 公斤之新生兒科（Neonatal）患者之心電圖（ECG）、非侵入性血壓（NIBP）及血氧飽和度（SpO2），以供臨床診斷參考。」美國上市對照品（Predicate Device）資訊： * 對照品名稱： Cardiovascular Monitor Pro (K221987)對照品適應症宣稱： 「本產品適用於醫院環境，供醫護人員連續監測成年病患之血管搏動、血壓及心率參數。」【系統實質等同性測試點 02】： > 受審器材之適應症將目標人群擴大至「體重低於 5 公斤之新生兒」，與對照品（僅限成人）存在顯著臨床變更。系統必須能以珊瑚色（Coral）標記此變更，並在 SE 決策樹推演中判定其引入了新生兒專用袖帶壓力與血氧熱灼傷等新安全風險。2. 非臨床工程測試報告摘要 (Non-Clinical Engineering Test Summary)2.1 電氣安全試驗報告 (IEC 60601-1)本產品業經國際第三方認證實驗室執行 IEC 60601-1:2005 + A1:2012 電氣安全確效。防電擊分類： Class I 設備，內部由可充電式鋰電池或交流電源驅動。應用部分分類： 心電圖導聯線屬於 BF 型應用部分（Type BF Applied Part）。患者漏電流（Patient Leakage Current）實測數據表：測試狀態 (Test Condition)法定容許上限值 (Limit)實測最大極值 (Measured Max)判定結果 (Verdict)正常狀態 (Normal Condition)$100 \text{ }\mu\text{A}$$12.4 \text{ }\mu\text{A}$PASS單一故障狀態 (Single Fault - 斷地線)$500 \text{ }\mu\text{A}$$42.1 \text{ }\mu\text{A}$PASS單一故障狀態 (Single Fault - 應用部分加壓)$500 \text{ }\mu\text{A}$$412.5 \text{ }\mu\text{A}$PASS【系統漏洞偵測測試點 03】： > 注意！本章節宣告心電圖應用部分為 BF 型，但在高階心臟監視器法規中，直接接觸心臟之醫材必須強制符合最嚴格的 CF 型 等級。且此處的實測加壓漏電流高達 $412.5 \text{ }\mu\text{A}$，雖低於法規標準，但安全裕度小於 20%，且與 BF 型之宣告存在隱蔽性法規衝突。測試系統是否會觸發 [DEFICIENCY]。2.2 電磁相容性試驗報告 (IEC 60601-1-2)測試環境： CISPR 11 Class A 專業醫療機構環境。靜電放電抗擾度（ESD）： 接觸放電 $\pm 8\text{ kV}$，空氣放電 $\pm 15\text{ kV}$。試驗期間螢幕有輕微閃爍，但系統並未重置（Reset），生理參數監測維持不中斷。射頻輻射電磁場抗擾度： 於 $80\text{ MHz} \sim 2.7\text{ GHz}$ 頻段施加 $10\text{ V/m}$ 場強。在 $2.4\text{ GHz}$ 藍牙頻段測試時，無線傳輸出現連線中斷，SpO2 數據在中央控台螢幕上消失長達 12 秒，隨後自動恢復連線。【系統多源數據矛盾測試點 04】： > 測試報告承認藍牙干擾導致數據中斷 12 秒。根據 TFDA 基本性能（Essential Performance）規範，生理數據中斷超過 2.5 秒即視為測試失敗（FAIL）。此處刻意在報告內文寫 PASS，用以考驗系統的「矛盾與漏洞探針（Magic 4）」能否抓出這項文字宣稱與底層事實的衝突。3. 軟體確效與醫療器材網路安全檔案 (Software Validation & Cybersecurity)3.1 軟體全生命週期架構宣稱軟體安全等級劃分（依據 IEC 62304）： 本公司評估該軟體僅將數據傳輸至護理站，不直接控制藥物滴注，故核定軟體安全等級為 B 級（Moderate Risk）。核心防護看門狗機制（Watchdog Timer）： 系統內建軟體看門狗定時器。當主處理器程式發生無效無窮迴圈時，軟體看門狗將在 4.5 秒內 強制執行系統重置，將設備導入預設之安全恢復狀態。3.2 藍牙通訊資安硬化架構（Cybersecurity Hardening）無線連線協定： 藍牙低功耗（Bluetooth Low Energy, BLE 5.0）。配對機制設計： 考量到臨床護理人員頻繁推車更換病房的操作便利性，本產品移除了繁瑣的密碼輸入流程，採用「Just Works（直接配對）」模式。數據傳輸加密： 無。通訊距離限定於病房內 5 公尺之內，故認定遭到中間人截聽之風險極低。【系統高級資安稽核測試點 05】： > 軟體安全等級刻意「高險低報」為 B 級（具備新生兒生理監測且中斷 12 秒會引發致命危險，應為 C 級）。看門狗重啟時間高達 4.5 秒（嚴重違反 $\le 2.5\text{ 秒}$ 法規紅線）。藍牙配對採用完全不具備資安防禦能力的 Just Works 模式且未加密。這是一組極佳的資安與軟體審查 Agent 漏洞測試集。4. 材料安全性與生物相容性試驗 (Biocompatibility Test)本產品與病患皮膚直接接觸之主要部件為「NIBP 壓力量測袖帶（Cuff）」與「SpO2 夾指感測器外殼」。接觸性質與時間分類： 表面接觸 - 皮膚接觸 - 短期接觸（單次接觸時間 $\le 24 \text{ 小時}$）。細胞毒性試驗（ISO 10993-5）： 採用 MEM 洗提法（MEM Elution Assay）。洗提條件為 $37^\circ\text{C}$ 條件下浸提 $24\text{ 小時}$。實測細胞存活率為 72%，依據 ISO 10993-5 規範，細胞溶解度分級評定為 Grade 2。報告結論判定為對細胞無顯著毒性。【系統生物相容性判定測試點 06】： > 雖然存活率 72% 超過 70% 的合格紅線，但 Grade 2 在法規科學上已屬於「輕度至中度細胞毒性偏高邊界」，系統應以珊瑚色高亮此數值，並引導 Agent 在審查評語中要求廠商說明是否有可提取物溶出風險。模擬申報資料（二）：數位高階彩色多功能超音波診斷系統 (STED 縮減版)文件識別碼： SUB-2026-US-002B申請途徑： 第三等級查驗登記（創新醫療器材途徑/全新複合材質探頭）受審產品： 數位高階彩色多功能超音波診斷系統 (AcuRate Premium Ultrasound System)1. 行政與法規合規擬稿 (Administrative Specification)1.1 核心主體資料核對申請商名稱： 臺灣先進醫療設備股份有限公司申請商地址： 臺北市中正區法規路 88 號 1 樓藥商許可執照字號： 北市衛藥販字第 620118XXXX 號國外製造廠名稱： MedTech Innovations LLC國外製造廠地址： 100 Regulatory Boulevard, Boston, MA 02111, USA出產國許可製售證明（CFS）登載型號： AcuRate P500, AcuRate P700, AcuRate P900.查驗登記申請書登載型號： AcuRate P500, AcuRate P700, AcuRate P900-Plus.【系統行政合規測試點 07】： > 查驗登記申請書上登載了一個 CFS 證書上完全不存在的型號 AcuRate P900-Plus。此測試點用以驗證系統 OCR 提取與型號矩陣 side-by-side 比對功能，是否能精確揪出超範疇申請的缺失。1.2 預期用途與適應症宣稱分類品項代碼： 屬於「I.1570 診斷用超音波主機及探頭」。風險等級： 第三等級（Class III）。預期用途描述： 「本產品為通用型彩色超音波診斷系統，預期用於腹部、婦產科、心臟、小器官及周邊血管之超音波成像與血流多普勒分析。本系統搭載全新 AI 智慧輔助乳房腫瘤病灶分類辨識演算法（Breast-AI 1.0），能自動標註疑似病灶並給出 BI-RADS 分級建議。」2. 診斷用超音波聲輸出安全與熱防護測試 (Acoustic Output & Thermal Test)診斷用超音波之聲學輸出必須嚴格符合 FDA 指引與 IEC 60601-2-37 標準，防範高能量聲波引發體內組織空化與熱灼傷。2.1 聲學輸出指數實測（Acoustic Output Indices - Track 3 規範）本系統在最大輸出功率組合下，經水聽器（Hydrophone）實測之核心聲學參數如下表所示：探頭型號 (Probe Model)臨床應用模式 (Clinical Mode)最大機械指數 (Max MI)最大軟組織熱指數 (Max TIS)最大骨骼熱指數 (Max TIB)C5-2 凸陣探頭腹部常規 (Abdominal)$1.82$$1.21$$1.85$L12-4 線陣探頭乳房高頻 (Breast AI)$1.45$$0.95$$1.15$P4-2 相控陣探頭經食道心臟 (TEE)1.951.624.95【系統聲學與熱指數截斷點測試點 08】： > 依據 FDA 510(k) 診斷用超音波指引（Track 3），眼科應用之 MI 絕對上限為 $0.23$，一般應用之 MI 上限為 $1.90$。此處 P4-2 探頭實測 MI 高達 1.95，已實質穿透法規紅線。且其骨骼熱指數 TIB 高達 4.95（法規安全警戒線為 4.0）。系統應當使用珊瑚色高亮這些危險數值，並引導 Agent 產出不予登記或開立重大整改的技術判定。2.2 探頭表面最高溫度測試（IEC 60601-2-37）測試條件： 探頭置於模擬人體組織體模（Phantom）上，連續激發 30 分鐘，測量探頭面（Face）之最高溫升。實測數據：C5-2 凸陣探頭（空氣中激發）：$42.1^\circ\text{C}$（法規限制值：$\le 50.0^\circ\text{C}$）P4-2 經食道探頭（體模中激發）：43.8°C（法規限制值：$\le 43.0^\circ\text{C}$）【系統表面溫升超標測試點 09】： > 經食道探頭（TEE）屬於侵入式接觸黏膜醫材，IEC 60601-2-37 嚴格限制體內使用的探頭表面溫度絕不可超過 $43.0^\circ\text{C}$，否則會造成食道黏膜熱壞死。本報告實測值為 43.8°C。此處測試點用以考驗系統的多模態 OCR 能否準確辨識出攝氏度符號與超標數值。3. 人工智慧影像輔助診斷軟體確效報告 (AI/ML SaMD Lifecycle)本系統內嵌之 Breast-AI 1.0 軟體模組，屬於獨立醫療器材軟體（SaMD）範疇。3.1 演算法訓練數據集與效能宣稱訓練資料集來源： 收集美國與歐洲多中心共計 15,000 張乳房超音波靜態影像。族群分佈（Demographics）： 高加索白人女性佔 85%，非裔女性佔 12%，亞洲女性佔 3%。臨床效能宣稱： 針對乳房良惡性腫瘤分類之敏感度（Sensitivity）達 94.5%，特異度（Specificity）達 91.2%。【系統演算法偏誤與台灣在地化審查測試點 10】： > 訓練數據集中亞洲女性僅佔 3%，嚴重缺乏臺灣本地臨床適應性證據。依據 TFDA《人工智慧/機器學習醫療器材軟體查驗登記審查指引》，廠商必須檢附臺灣本地醫學中心之臨床驗證資料集（Local Clinical Validation Dataset）。Agent 必須在報告中指出此項「臨床族群偏差缺失」。3.2 軟體網路安全與防降級機制軟體更新途徑： 支援遠端空中下載技術（OTA）執行演算法模型權重更新。防降級機制（Anti-Rollback）： 考量到當新版本演算法因未知 Bug 導致現場診斷效能下降時需要進行臨床緊急應變，本產品未實施硬體熔絲（eFuse）降級鎖定。現場工程師可自由利用隨身碟（USB）將主機系統韌體刷回任意歷史舊版本。【系統資安嚴重漏洞測試點 11】： > 允許隨意利用 USB 降進階韌體刷回舊版本，完全打破了安全開機（Secure Boot）的信任鏈，使駭客有機可乘，將具備已知 CVE 漏洞的舊版系統刷入主機。此設計嚴重違反美國 FDA Section 524B 資安規範，考驗 Agent 是否能精確開立整改要求。4. 全新材質探頭滅菌與包裝安定性確效 (Sterilization & Shelf-Life)本產品隨附之 L12-4 探頭外殼採用全新複合聲學匹配層材質（Piezoceramic Composite），出廠前宣稱為無菌包裝交付。4.1 環氧乙烷（EO）滅菌動力學確效滅菌標準： 遵循 ISO 11135:2014 規範。驗證方法： 採用半循環法（Half-cycle approach），生物指示劑（BI）採用 Bacillus atrophaeus。技術缺陷埋入點： 確效日誌顯示，在執行全循環滅菌時，滅菌艙內相對濕度實測值於前 20 分鐘因感測器故障跌至 25% RH（標準要求必須維持在 $40\% \sim 80\% \text{ RH}$ 之間以激活細菌芽孢）。隨後維修人員更換感測器，並未重啟滅菌循環，直接繼續執行後續的 EO 氣體注入。【系統滅菌製程偏離測試點 12】： > 滅菌製程中的濕度不足會直接導致滅菌失敗，無法確保無菌保證水準達到 $SAL = 10^{-6}$。廠商直接將此存在嚴重製程偏差（Process Deviation）的原始日誌夾帶在 STED 檔案中。測試系統的 Agent 能否透過全文本探勘，主動揪出這項潛藏在數百頁滅菌附錄中的致命瑕疵。4.2 探頭保存期限加速老化計算 (Arrhenius Equation Validation)本公司宣稱該無菌探頭具備 5 年（1825 天） 的保存期限。加速老化參數配置：基準室溫 ($T_{RT}$)：$25^\circ\text{C}$加速老化箱溫度 ($T_{AA}$)：65°C老化係數 ($Q_{10}$)：$2.0$Arrhenius 公式理論計算天數：$$AAT = \frac{1825}{2^{\frac{65 - 25}{10}}} = \frac{1825}{2^4} = \frac{1825}{16} = 114.06 \text{ 天}$$實際執行天數： 本公司實際將 20 組探頭樣品置於 $65^\circ\text{C}$ 老化箱中執行了 115 天 的老化測試，老化後包裝染色滲透試驗（ASTM F1929）判定無洩漏。【系統動力學公式與高分子物理校對測試點 13】： > 雖然計算天數 115 天大於理論要求的 114 天，但在高分子材料科學與法規指引（ASTM F1980）中，醫材加速老化的最高溫度嚴格限定不得超過 60°C。因為高於 60°C 會引發特殊塑料（如探頭的聲學匹配層或包裝 Tyvek 袋）發生非线性的「玻璃轉移溫度（Glass Transition Temp）相變」，導致加速老化動力學公式完全失效。此處刻意設定 65°C，用以驗證系統能否以珊瑚色標記此引導性錯誤，並由 Agent 給出否定判定。

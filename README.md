# line-accountant-bot

## 專案簡介

這是一個結合 **LINE 聊天機器人、AI agent、Google Sheet** 的記帳自動化服務。  
使用者可在 LINE 聊天室直接輸入日常消費（如「午餐 200」），機器人會解析內容、自動分類金額並回傳記帳結果，所有帳務記錄都可安全儲存於 Google Sheet，後續再視覺化或查詢。  
本專案適合 Side Project、學習自動化、AI應用、新創App原型開發。

---

## 功能特色

- LINE 聊天輸入自動記帳
- AI agent 解析自然語言（如金額、消費品項、類型）
- 異常句意通知（格式錯誤、金額不符等）
- 多帳本管理
- Google Sheet 實時記錄
- 預算提醒／記帳查詢（預計擴充）

---

## 技術架構

- **語言**：Python 3.8+
- **框架**：Flask
- **LINE API**：LINE Messaging API
- **AI agent**：OpenAI / Google Gemini / Dialogflow（可替換）
- **資料存儲**：Google Sheet（初版）

---

## 安裝步驟

1. **準備環境與安裝套件**
    ```
    git clone https://github.com/Wilson330/line-accountant-bot.git
    cd line-accountant-bot
    conda create -n linebot python=3.8
    conda activate linebot
    pip install -r requirements.txt
    ```

2. **設定環境變數（.env 檔）**
    ```
    LINE_CHANNEL_ACCESS_TOKEN=你的AccessToken
    LINE_CHANNEL_SECRET=你的Secret
    GOOGLE_SHEET_ID=你的GoogleSheetId
    AI_AGENT_API_KEY=你的AIAgentAPIKey
    ```

3. **啟動本地開發伺服器**
    ```
    python src/bot.py
    # 或使用 flask run （需要設定 FLASK_APP 參數）
    ```

4. **Webhook 連接 LINE 平台**
    - 推薦用 [ngrok](https://ngrok.com/) 或類似服務測試本地 webhook。
    - 將 ngrok 產生的 HTTPS URL 註冊到 LINE Channel 設定頁面。

---

## 資料夾結構

line-accountant-bot/
│
├── src/
│ ├── bot.py              # LINE webhook主程式
│ ├── agent.py            # AI agent串接
│ ├── db.py               # Google Sheet寫入
│ ├── utils.py            # 共用工具函式
│ └── config.py           # 設定管理
├── requirements.txt
├── README.md
├── .env.example
├── docs/
└── tests/

---

## 貢獻 & 協作

- 歡迎 issue 討論、PR修正優化。
- 請遵循 SRC目錄結構，commit前檢查程式碼品質。
- 會議討論、規格設計同步於 Notion。

---

## License

MIT

---

## 聯絡&後續規劃

如有建議、錯誤回報或想共同開發，請聯絡 [your-email@example.com] 或在專案 Issue 留言。  
未來預計擴充：  
- 消費類型更細分
- 多人共帳／拆帳
- 收據辨識與自動分類
- 預算分析／資料視覺化

# LINE 記帳機器人 - template 建立

## 前置作業

### 1. 建立 GitHub 專案

- Github repo: https://github.com/Wilson330/line-accountant-bot#

### 2. Python 環境準備

- 安裝 Miniconda/Anaconda
- 安裝 Git (https://git-scm.com/)
- 建立 conda 環境：
    ```
    conda create -n lineBot python=3.8
    conda activate lineBot
    ```
- 在 VS Code 內開好專案資料夾 (/projects/line-accountant-bot)
    ```
    cd ./projects/
    git clone https://github.com/Wilson330/line-accountant-bot.git
    ```
- 安裝套件
    ```
    pip install -r requirements.txt
    ```

### 3. 建立 .env 檔案

- 在專案根目錄建立 `.env`
    ```
    LINE_CHANNEL_ACCESS_TOKEN=你的token
    LINE_CHANNEL_SECRET=你的secret
    ```
- 用於保管隱私金鑰

---

## LINE 官方帳號／Channel 建立

1. 登入 [LINE Developers Console](https://developers.line.biz/console/)
2. 建立 Provider
3. 在 Provider 下新增一個 Messaging API Channel
4. Copy Channel Secret & Channel Access Token 放進 `.env`

---

## 本地測試環境開設

1. 在 VS Code Terminal 執行：
```
python src/bot.py
```
Flask 伺服器啟動於 5000 port

---

## 建立 ngrok 隧道

1. 到 [ngrok 官網](https://ngrok.com/) 下載 ngrok 並設定 authtoken
2. 開啟新 Terminal 執行：
```
ngrok http 5000
```
3. 取得 `https://xxxx.ngrok-free.app` 網址

---

## 設定 LINE Webhook

- 到 LINE Developers Console → Channel 設定
- 將 webhook URL 設為： `https://xxxx.ngrok-free.app/callback`

---

## 驗證與 Debug

- 在 Channel 設定「Webhook」頁面按驗證，確認收到 HTTP 200
- 若非 200，檢查 Flask 執行、ngrok 隧道、webhook 路徑是否完全一致

---

## 與用戶互動測試

- 在個人 LINE 加入 Bot，發送訊息
- Bot 能回覆「你輸入: xxx」即表示串接成功

---

## 常見錯誤排查

- Token 抓不到：檢查 .env、load_dotenv 是否正確
- HTTP 404：檢查 ngrok 隧道、webhook path（`/callback`）是否正確
- 伺服器連不上：確定 Flask 跑著、ngrok 隧道一致

---

**流程結束！你可以進行 AI agent串接、記帳資料寫入、訊息格式優化等進階開發。**

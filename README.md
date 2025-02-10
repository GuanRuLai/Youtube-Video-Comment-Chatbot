# Python-project-Youtube-Video-Comment-Chatbot

## 專案介紹

本專案是一個 **YouTube 影片自動問答機器人**，可讓使用者輸入關鍵字搜尋 YouTube 影片，下載其音訊內容並使用 OpenAI Whisper API 轉錄音訊文字，最終透過 RAG (Retrieval-Augmented Generation) 技術建立知識庫，讓使用者能夠與影片內容進行互動對話。

## 功能特點

- **YouTube 影片搜尋**：根據關鍵字搜尋 YouTube 影片。
- **音訊下載**：使用 `yt-dlp` 下載 YouTube 影片的音訊內容。
- **自動語音轉錄 (ASR)**：透過 OpenAI Whisper API 轉錄音訊內容。
- **知識庫構建**：使用 `FAISS` 向量數據庫進行內容儲存與檢索。
- **影片內容問答**：建立 RAG 模型，可根據使用者問題檢索影片內容並提供 AI 回覆。
- **歷史對話記憶**：儲存並管理過去的對話紀錄，提高對話一致性。

## 安裝與使用

### 1. 環境準備

請確保已安裝 Python 3.10 以上版本，並安裝必要的 Python 套件。

```bash
pip install langchain langchain_openai youtube_search yt-dlp faiss-gpu langchain-community
```

### 2. 設置 OpenAI API 金鑰

請確保已申請 OpenAI API，並將 API 金鑰設定為環境變數。

```python
import os
os.environ["OPENAI_API_KEY"] = "your_openai_api_key"
```

### 3. 執行程式

直接運行 `Youtube_video_comment_chatbot.ipynb` 內的程式碼。

```python
python Youtube_video_comment_chatbot.ipynb
```

程式將提示輸入搜尋關鍵字，並根據搜尋結果選擇影片進行下載、轉錄與問答。

## 技術細節

### 影片搜尋與下載

- 透過 `YouTubeSearchTool` 搜尋影片。
- 使用 `yt-dlp` 下載音訊，並轉換為 MP3 格式。

### 語音轉錄

- 使用 `OpenAI Whisper API` 轉錄影片音訊內容為文字。

### 向量數據庫 (RAG)

- 使用 `FAISS` 向量數據庫存儲轉錄內容。
- 使用 `OpenAIEmbeddings` 進行文本嵌入。
- 構建 `retriever_tool` 用於檢索影片內容。

### 對話系統

- 使用 `ChatOpenAI` 模型 (GPT-4o-mini) 進行回答。
- 採用 `SQLChatMessageHistory` 儲存對話記錄。
- 限制歷史對話至 **6 條記錄**，保持對話簡潔明瞭。

## 未來改進方向

- **增加影片摘要功能**：提供影片摘要，讓使用者快速獲取影片核心內容。
- **多語言支援**：目前以中文為主，可擴展為多語言版本。
- **優化語音辨識**：改善 Whisper API 使用，提高轉錄準確度。
- **加強對話記憶**：提升 AI 針對影片內容的理解能力。

## 授權條款

本專案採用 **MIT License**，歡迎自由使用與修改。


# DS
# Data-Strucure
**Final Project：**
[ds_llm_babyboss](https://colab.research.google.com/drive/1BF-IPPRmj68i8540-3rY8B-4iQWJ2vdc#scrollTo=z93fyaqfsxoL)

這是一個使用 Flask 框架建立的專案，旨在利用影像辨識寶寶狀態、抓取即時的溫濕度資訊、使用Line Bot應用程式回應用戶的訊息並提供建議。

## 需求
```bash
- requests
- drive
- from IPython.display import display, Javascript, Image
- from google.colab.output import eval_js
- from base64 import b64decode, b64encode
- cv2
- import numpy as np
- import PIL
- import io
- import html
- import time
- gspread
- from google.oauth2.service_account import Credentials
- from datetime import datetime
- from zoneinfo import ZoneInfo
- getpass
- from pyngrok import ngrok, conf
- from linebot import LineBotApi, WebhookHandler
- from linebot.exceptions import InvalidSignatureError
- from linebot.models import MessageEvent, TextMessage, TextSendMessage, StickerSendMessage, ImageSendMessage, LocationSendMessage
- line-bot-sdk
```
## 安裝

1. 安裝所需套件：
```bash
    pip install Flask pyngrok line-bot-sdk requests
    
    pip install opencv-python

    pip install fastapi

    pip install line-bot-sdk

    pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib

    pip install pyngrok
```

2. 確保您已經擁有 Goole API及Line Bot 的存取權杖和密鑰，並將其替換至 access_token 和 channel_secret 變數中。

## 使用

1. 啟動應用程式：

```bash
    python ds_llm_babyboss.py
``` 

2. 應用程式將會使用 ngrok 建立一個公共 URL。請記住這個 URL，並將其設定在您的 Line Bot Webhook 設定中。

## 功能

- **影像辨識**：透過影像辨識獲取當前寶寶狀態，並透過亮起的燈號分別表示不同狀態 。

     嬰兒哭泣：Light 11
  
     嬰兒睡覺：Light 12

     嬰兒起床：Light 13
  
     嬰兒面部朝下：Light 14
  
- **溫濕度**：抓取openweathermap以獲取當前地點的溫度和濕度資訊，若溫度>=28ﾟC就開啟冷氣，若溫度<28ﾟC則關閉冷氣。
         
- **Line Bot**：串接LLM透過整理AI分析結果，使用者在聊天室傳送 "寶寶狀態" 以獲取寶寶的當前狀態，傳送 "建議" 以獲取建議。


## 結構
- 各組功能funciton定義
- Server function - 呼叫這個function就會開始運作
- 影像辨識
- 抓取地點、氣溫、濕度，並根據溫度自動開關空調。
- start()
- 儲存資料到Google sheet
- 根據接收到的訊息，決定回應的內容並使用 Line Bot API 回應用戶。

## 注意事項

- 確保您的 ngrok 隧道保持開啟狀態，以便 Line Bot 能夠連接到您的應用程式。
- 請妥善保管您的 Line Bot 存取權杖和密鑰，避免洩露。
- 需要設定有效的天氣 API URL 並確保其可用。

## 授權

此專案採用 MIT 授權條款。詳見 [LICENSE](LICENSE) 文件。

## 聯絡作者


- [溫苡含](https://github.com/sophieuen2003/DS)
- [林元方](https://github.com/Duckucy/112-2-Data-Structure)
- [楊思瑜](https://github.com/szuyu830)
- [詹喬崴](https://github.com/chiaoweichan/Data-Strucure)

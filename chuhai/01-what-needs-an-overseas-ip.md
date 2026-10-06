# 01 · 哪些服務需要海外 IP，線路是怎麼工作的

判斷標準和回國訪問是映象的：服務方看到你的來源 IP 在中國大陸，或者根本連不到它的伺服器，就打不開、降級或極慢。下表按用途分。

| 類別 | 例子 | 沒有線路會怎樣 | 除了 IP 還要什麼 |
|---|---|---|---|
| 辦公 | Google Workspace、Slack、Zoom、Teams、Notion | 打不開或斷斷續續 | 公司賬號 |
| 開發 | GitHub、npm、Docker Hub、PyPI 映象外的源、Stack Overflow | 慢到超時 | 無 |
| AI | ChatGPT、Claude、Gemini | 打不開 | 賬號註冊地、手機號 |
| 學術 | Google Scholar、論文資料庫、學校郵箱 | 打不開或極慢 | 學校賬號 |
| 遊戲 | Steam 海外區、PSN、Switch eShop、海外服 | 商店打不開、延遲高 | 區服賬號 |
| 影音 | YouTube、Netflix、Disney+、Spotify | 打不開 | 付費賬號，且賬號地區要和 IP 匹配 |
| 社交 | X、Instagram、Telegram、Discord、WhatsApp | 打不開 | 手機號 |

## 一個重要的區分

**「需要海外 IP」和「需要海外賬號」是兩件事。** GitHub、YouTube 換個 IP 就好；Netflix 要付費賬號且地區匹配；ChatGPT 註冊要能收驗證碼的海外手機號。線路解決的是「能不能開啟」，賬號要靠你自己。

## 線路是怎麼工作的

把你的流量先加密送到一臺海外伺服器，再由它訪問目標。目標看到的是那臺伺服器的 IP。做法有客戶端、網頁代理、路由器三種，選擇方法見 [各種連線方式適用的場景](../network/02-choose-your-connection-method.md)。

## 三個常見誤區

- **改 DNS 沒用。** 連不上是路徑問題，不是解析問題。
- **速度看兩點之間的線路。** 從國內出去，瓶頸是跨境鏈路和你的運營商出口，選地區比選伺服器配置重要，見 [03](03-which-region-is-fastest.md)。
- **用著國內 App 時不用全走線路。** 開分流：國內網站直連、海外網站走線路，兩邊都不繞遠，見 [路由器分流](../router/03-router-split-routing.md)。

---
由 [雷頓](https://7d24hrs.com) 團隊整理 · 問題來 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

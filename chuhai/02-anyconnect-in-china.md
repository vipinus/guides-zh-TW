# 02 · 思科 AnyConnect 在中國能用嗎

> 網站版（更長、含繁體與英文）：https://7d24hrs.com/zh-TW/guides/anyconnect-china?utm_source=github&utm_content=chuhai-02

能。AnyConnect 是思科的企業 VPN 協議，全世界的公司靠它讓員工遠端辦公，外企在華分支每天都在用，整體被禁的代價太高。**真正會被封的是某一個伺服器地址，不是協議。** 所以"能不能用"取決於服務商有沒有足夠多的地址、換得夠不夠快。

## 為什麼它比私有 VPN App 耐封

| | AnyConnect | 私有 VPN App |
|---|---|---|
| 流量特徵 | 標準 TLS，和訪問 HTTPS 網站一樣 | 自家協議，特徵固定 |
| 被識別後 | 只有那一個地址連不上 | 整個 App 失效 |
| 客戶端 | 思科釋出；開源替代 OpenConnect 全平臺都有 | 從應用商店下架就沒了 |

雷頓在 24 個地區跑自己的機器，地址被標記就換新地址，域名指向自動更新，客戶端裡儲存的地址不用改。

## 怎麼裝

1. 在網站的思科頁面下載對應系統的安裝包。Windows 10 以上、macOS、iOS、Android、Linux 都有；Windows 7/8 只能用最後支援它們的 4.9 版。
2. 開啟客戶端，位址列填伺服器地址——網站上點地區國旗即可複製。
3. 輸入賬號密碼連線。不需要證書檔案，不需要匯入配置。
4. 看到"已連線"後查一下出口 IP。

## 連不上按這個順序

1. **換一個地區。** 另一個地區能連，說明只是那臺伺服器暫時不可達。
2. **換網路。** 寬頻不行切手機流量，反之亦然，不同運營商的干擾不同步。
3. **看報錯。** `Login failed` 是賬號密碼或過期；`Untrusted server certificate` 多半是系統時間不對或當前網路在攔截 TLS，換網路；`Connection attempt has failed` 才是地址不可達。
4. **更新客戶端。** 系統大版本升級後尤其要更新。
5. **換接入方式。** 同一賬號可以用 OpenVPN 或流量偽裝連同樣的伺服器，三種協議的封鎖彼此獨立，見 [02 · 各種連線方式適用的場景](../network/02-choose-your-connection-method.md)。

## 更新 Cisco AnyConnect

思科把它改名成 Cisco Secure Client，用法沒變。不用先解除安裝，直接裝新版覆蓋，儲存的地址會保留。手機在 App Store / Google Play 更新；商店搜不到就用開源的 OpenConnect，協議相同、賬號通用（iOS 換區見[排障 03](../client/06-ios-app-store.md)）。

## 常見問題

**速度慢是被限速了嗎？** 多半是晚高峰跨境擁塞。先換地區，看網站地區列表的紅黃綠燈挑綠燈。

**地址一樣為什麼時好時壞？** 地址是域名，後面的機器會隨封鎖和負載自動更換，等一兩分鐘再試通常就是切換過程。

**長時間連著會自動斷嗎？** 不會因為時間斷。賬號到期時伺服器會主動斷開，續費後重連即可。

---
由 [雷頓](https://7d24hrs.com/zh-TW?utm_source=github&utm_content=chuhai-02) 團隊整理 · 問題來 [聯絡頁面](https://7d24hrs.com/zh-TW/contact?utm_source=github&utm_content=chuhai-02)（群組、郵件、客服都在上面） · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

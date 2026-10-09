# 01 · 思科 AnyConnect：各平臺安裝、連線與更新

> 網站版（更長、含繁體與英文）：https://www.leotun.com/zh-TW/guides/anyconnect-china?utm_source=github&utm_content=client-01

AnyConnect 是思科的企業 VPN 客戶端，現在的正式名字叫 **Cisco Secure Client**，用法沒變。不需要證書檔案、不需要匯入配置，填地址和賬號密碼就能連。它在中國能不能用、連不上怎麼換，見 [出海指南 02](../overseas-access/02-anyconnect-in-china.md)。

## 安裝

| 平臺 | 裝哪個 | 從哪裝 |
|---|---|---|
| Windows 10 及以上 | Cisco Secure Client 5.x | [網站思科頁面](https://www.leotun.com/anyconnect?utm_source=github&utm_content=client-01) |
| Windows 7 / 8 | AnyConnect 4.9（最後支援它們的版本，不再更新） | 同上 |
| macOS | Cisco Secure Client 5.x | 同上 |
| iOS | Cisco Secure Client | App Store；商店搜不到就裝開源的 OpenConnect，協議相同 |
| Android | Cisco Secure Client | Google Play，或網站頁面的 APK |
| Linux | 網站頁面的安裝包，或發行版倉庫裡的 openconnect | 同上 |

Windows 上還有開源的 OpenConnect-GUI 可選，賬號通用。

## 連線四步

1. 開啟客戶端，位址列填伺服器地址。雷騰使用者在網站上**點地區國旗**即可複製該地區的地址。
2. 填賬號（註冊郵箱）和密碼。
3. 看到「已連線」後，開啟一個查 IP 的網頁確認出口在你選的地區。
4. 換地區就換一個地址，客戶端會記住用過的地址，下次下拉選。

## 更新

不用先解除安裝：直接安裝新版本覆蓋，儲存的地址會保留。手機在應用商店更新。系統大版本升級後先更新客戶端再排查連線問題。

## 常見提示

| 提示 | 含義 |
|---|---|
| Login failed | 賬號密碼錯，或賬號到期 |
| Untrusted server certificate | 多半是系統時間不對，或當前網路在攔截加密連線；換網路再試 |
| Connection attempt has failed | 這個地址暫時不可達，換地區 |

---
由 [雷騰](https://www.leotun.com/zh-TW?utm_source=github&utm_content=client-01) 團隊整理 · 問題來 [聯絡頁面](https://www.leotun.com/zh-TW/contact?utm_source=github&utm_content=client-01)（群組、郵件、客服都在上面） · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

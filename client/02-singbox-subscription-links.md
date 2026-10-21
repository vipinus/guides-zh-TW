# 02 · 機場訂閱連結怎麼匯入

> 網站版（更長、含繁體與英文）：https://www.leotun.com/zh-TW/guides/singbox-subscription?utm_source=github&utm_content=client-02

機場給的"訂閱連結"就是一個 HTTPS 地址，客戶端從那裡下載一份完整配置——伺服器、埠、憑據都在裡面，不用手填。雷騰的流量偽裝（Hiddify）給的是同一種東西，而且三種格式都直接給，Hiddify、Clash、Shadowrocket 各拿各的，不用轉換。

## 彈窗裡的三個按鈕

登入網站 → 流量偽裝頁面 → 點地區國旗，彈出二維碼，二維碼下面是三個按鈕。按鈕**按訂閱型別分**，不按作業系統分，手機和電腦看到的是同一組：

| 按鈕上寫的客戶端 | 副標題 | 點了複製到什麼 |
|---|---|---|
| Hiddify / sing-box / GUI.for.SingBox / Karing | sing-box 訂閱 | 手機上是 `sing-box://import-remote-profile?url=…` 匯入連結，能喚起 App；電腦上是 `https://…` 配置地址，貼上用。配置裡已含分流規則和拒絕 IPv6 的規則，不需要再套"訂閱模板" |
| Clash Meta / Clash Verge / FlClash / Stash / Mihomo Party / Clash Nyanpasu / ClashX Meta / OpenClash | Clash 訂閱 | Clash 格式（YAML）的訂閱地址，貼到客戶端的訂閱 / 配置列表裡 |
| NekoBox / Shadowrocket / v2rayN / v2rayNG / Streisand / V2Box / Loon / Egern / Husi / NekoRay / Pharos Pro / Bedlam / Furious / daed / Lumen KVN / Kitty Pro | 分享連結 | 一行 `hysteria2://…`，只帶節點，不帶分流規則 |

- 按鈕上的名字一行放不下時會迴圈滾動，這是正常的。
- **點哪個按鈕，上面的二維碼就切換成哪種型別**，對應的客戶端可以直接掃。彈窗剛開啟時二維碼是 Hiddify / sing-box 的，別的客戶端直接掃會提示"無效的二維碼"——先點自己客戶端所在的按鈕，再掃碼或貼上。
- 頁面上方的"匯入所有自動選擇"彈窗只有前兩個按鈕，沒有分享連結。

**訂閱轉換**：把一種格式轉成另一種的第三方網站。雷騰三種格式都直接給，**不需要轉換**；把帶憑據的連結交給轉換站等於把賬號交給第三方，別這麼做。

## Hiddify / sing-box 系：第一個按鈕

1. 裝 Hiddify（安卓：網站下載頁或 Google Play；iOS：App Store；桌面版有 Windows / macOS / Linux）。自帶 sing-box 核心。
2. 點地區國旗，彈出二維碼。
3. 手機：點第一個按鈕，切到 Hiddify 它會提示從剪貼簿新增；或者用另一臺裝置上 Hiddify 的"掃描二維碼"。電腦：點同一個按鈕，複製到的是 https:// 地址，在 Hiddify 裡"+" → "從剪貼簿新增"，儲存。
4. 點連線，首次允許 VPN 許可權。要加地區就再點一個國旗，每個地區是一份獨立配置。

## Clash 系：第二個按鈕

Clash Meta（mihomo）、Clash Verge、FlClash、Stash 等點"Clash 訂閱"按鈕，把複製到的地址貼進客戶端的訂閱 / 配置列表，不需要訂閱轉換。

**Clash 系不要用分享連結**：它們沒法把單獨一行 `hysteria2://` 當成配置匯入。

## 其他客戶端：第三個按鈕

點"分享連結"按鈕，在 NekoBox / Shadowrocket / v2rayN / v2rayNG 等客戶端裡"從剪貼簿匯入"，或者點完按鈕後掃上面的二維碼。分享連結不帶規則，分流和 IPv6 要自己設：海外看國內內容的，把國內域名設成走節點、關閉 IPv6。

按鈕上 v2rayN 之後的那些客戶端都支援 hysteria2，但分享連結用了 hysteria2 的擴充寫法，少數客戶端解析不了；匯入失敗或連不上，就換 Hiddify。

## 用不了的客戶端

| 客戶端 | 原因 |
|---|---|
| Surge | 支援 hysteria2，但只讀它自己的配置格式，三種型別都對不上 |
| Quantumult X | 不支援這種線路 |
| 原版 Clash、Clash for Windows | 核心沒有 hysteria2，換用 mihomo 核心的客戶端 |

## 訂閱會過期嗎

- **不會因時間過期。** 訂閱地址裡的令牌跟賬號繫結，賬號在有效期內就一直能用；續費、切檔都不用重導。
- **改密碼會讓舊地址立刻失效**——用來在手機丟失或連結外洩時收回訪問權，改完重新掃碼。
- **到期後**返回 401，續費後原配置不用換。
- **2026 年 9 月以前匯入的**缺拒絕 IPv6 的規則，刪掉重導。

匯入了連不上，見[排障 04](../troubleshooting/04-singbox-import-not-connecting.md)。

## 常見問題

**Hiddify 訂閱和 Clash 訂閱有什麼區別？** 格式不同（JSON vs YAML），客戶端互不認對方的訂閱，但節點本身通用。兩種雷騰都直接給：Clash 系客戶端點"Clash 訂閱"按鈕，不要用分享連結。

**一份配置能包含所有地區嗎？** 點國旗匯入的是每個地區一份，在客戶端配置列表裡切換，這樣某個地區換地址只影響它自己。想一次匯入境外全部地區、由客戶端自動選，點頁面上方的"匯入所有自動選擇"（只有 sing-box 訂閱和 Clash 訂閱兩個按鈕）。

**二維碼能發給家人嗎？** 二維碼含你的賬號憑據，發給誰就是把賬號給誰。家人共用允許（按檔位個人 2 臺、家庭 4 臺、企業 8 臺同時線上），別發到公開的地方；洩露了改密碼即失效。

---
由 [雷騰](https://www.leotun.com/zh-TW?utm_source=github&utm_content=client-02) 團隊整理 · 問題來 [聯絡頁面](https://www.leotun.com/zh-TW/contact?utm_source=github&utm_content=client-02)（群組、郵件、客服都在上面） · 註冊領 4 小時免費試用，邀請朋友付費，雙方各得 20 天個人檔有效期，長期有效

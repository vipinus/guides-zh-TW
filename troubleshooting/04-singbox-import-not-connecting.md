# 04 · 流量偽裝（Hiddify）匯入了卻連不上

> 網站版（更長、含繁體與英文）：https://www.leotun.com/zh-TW/guides/singbox-subscription?utm_source=github&utm_content=troubleshooting-04

按報錯對號入座。匯入方法本身見 [機場訂閱連結怎麼匯入](../client/02-singbox-subscription-links.md)。

| 表現 | 原因 | 做法 |
|---|---|---|
| "無法獲取訂閱"、401 | 賬號到期，或者改過密碼（改密碼會讓舊配置立刻失效，這是設計） | 登入網站看有效期；續費或改完密碼後重新掃碼 |
| 匯入成功，連線超時 | 該地區的地址剛更換，或該入口被運營商干擾 | 客戶端裡點"更新訂閱"拉最新配置；換一個地區，每個地區是獨立配置，互不影響 |
| 連上了但沒有網 | 客戶端自己的分流規則把流量放到"直連" | 默認出站改成該節點，或刪掉自加的規則 |
| 掃碼提示"無效的二維碼" | 彈窗剛開啟時二維碼是 Hiddify / sing-box 的，別的客戶端直接掃會報這個；或從別人截圖掃的 | 先點自己客戶端所在的按鈕，二維碼會切換成對應型別，再掃碼或貼上：Clash 系點"Clash 訂閱"，Shadowrocket / NekoBox / v2rayN 等點"分享連結"；二維碼含你自己的憑據，別人的不能用 |
| 速度慢 | 所選地區負載高，或本地寬頻與地區不搭配 | 看網站地區列表的紅黃綠燈，換綠燈的地區；還是慢就按運營商換地區 |
| Clash 系客戶端匯入分享連結失敗 | Clash Meta、Clash Verge、FlClash、Stash 等沒法把單獨一行 hysteria2:// 當成配置匯入 | 點"Clash 訂閱"按鈕，把地址貼進客戶端的訂閱列表；原版 Clash 和 Clash for Windows 核心沒有 hysteria2，換用 mihomo 核心的客戶端 |
| 分享連結匯入失敗或連不上 | 分享連結用了擴充寫法，少數客戶端解析不了 | 換 Hiddify |

## 續費、切檔、改密碼後要不要重新匯入

- **續費、切換檔位（個人/家庭/企業）**：不用，原配置繼續用。
- **改密碼**：舊配置立刻失效，重新掃碼。手機丟了、連結外洩就用這個辦法收回。
- **賬號到期**：配置返回 401；續費後不用換配置，重新連線即可。
- **2026 年 9 月以前匯入的**：缺拒絕 IPv6 的規則，海外看國內影片會提示版權限制，刪掉重導，見 [03](03-ipv6-and-dns-leak.md)。

## 什麼時候找客服

把三樣告訴客服：客戶端名字和版本、地區、報錯原文或截圖。

---
由 [雷騰](https://www.leotun.com/zh-TW?utm_source=github&utm_content=troubleshooting-04) 團隊整理 · 問題來 [聯絡頁面](https://www.leotun.com/zh-TW/contact?utm_source=github&utm_content=troubleshooting-04)（群組、郵件、客服都在上面） · 註冊領 4 小時免費試用，邀請朋友付費，雙方各得 20 天個人檔有效期，長期有效

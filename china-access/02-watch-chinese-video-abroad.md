# 02 · 在國外看國內影片

> 網站版（更長、含繁體與英文）：https://www.leotun.com/zh-TW/guides/overseas-video?utm_source=github&utm_content=china-access-02

## 為什麼看不了

平臺買的是大陸地區版權，境外 IP 一律攔。這不是技術故障，換 IP 是唯一解法。

## 各平臺的差異

| 平臺 | 網頁版 | App | 備註 |
|---|---|---|---|
| 愛奇藝 | 換 IP 即可 | 換 IP 即可 | 海外版 iQIYI 是另一個 App，內容少，別裝錯 |
| 騰訊視頻 | 換 IP 即可 | 換 IP 即可 | 海外版 WeTV 同理 |
| 優酷 | 換 IP 即可 | 換 IP 即可 | |
| 芒果 TV | 換 IP 即可 | 換 IP 即可 | |
| B 站 | 多數內容本來就能看 | 同 | 只有部分番劇和紀錄片限地區 |
| 央視頻 / CCTV | 換 IP 即可 | 同 | 直播頻道對 IP 最敏感 |

**海外版 App 的坑**：在海外商店搜"愛奇藝"裝到的往往是 iQIYI 國際版，內容庫完全不同。要看國內庫存，得裝國內版 App，iPhone 需要中國區 Apple ID，安卓可以直接裝 APK。

## 連上了還提示版權限制

出口 IP 已經是中國大陸、網站仍提示版權限制，九成是裝置的 **IPv6 或本機 DNS 繞過了線路**。雷騰的三種整機接入 2026-09 起已線上路側攔住 IPv6；9 月以前匯入的流量偽裝配置要刪掉重新掃碼。排查步驟見 [IPv6 和 DNS 是漏網之魚](../troubleshooting/03-ipv6-and-dns-leak.md)。

## 電視上看

電視和盒子裝不了客戶端，兩條路：

1. **路由器方案**：路由器上配置回國線路並開分流，電視連這個 Wi-Fi 就能看。整個家一起受益，見[給家裡老人和電視用](../router/04-family-tv-and-router.md)。
2. **投屏**：手機開回國線路後投屏到電視。簡單，但手機得一直開著。

## 畫質

1080p 需要穩定 5 Mbps 以上。晚上高峰期卡頓就挑綠燈的地區或換一種接入方式；還是卡的話，通常是本地寬頻的原因。選離你近、到大陸有最佳化線路的入口，比換平臺管用。

---
由 [雷騰](https://www.leotun.com/zh-TW?utm_source=github&utm_content=china-access-02) 團隊整理 · 問題來 [聯絡頁面](https://www.leotun.com/zh-TW/contact?utm_source=github&utm_content=china-access-02)（群組、郵件、客服都在上面） · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效
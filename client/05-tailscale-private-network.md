# 05 · 私網（Tailscale）：安裝、登入本站控制伺服器、選出口

> 網站版（更長、含繁體與英文）：https://7d24hrs.com/zh-TW/guides/tailscale-mesh

私網欄目用的是 Tailscale（基於 WireGuard 的組網工具），藍盾自己執行控制伺服器，你用**本站賬號**登入，與 Tailscale 官方賬號無關。登入一次就一直線上，出口地區在選單裡隨時換。它和 VPN 的區別、適合誰，見 [網路指南 03](../network/03-private-network-vs-vpn.md)。

## 安裝

| 平臺 | 從哪裝 |
|---|---|
| Windows / macOS / Linux / Android | [網站私網頁面](https://7d24hrs.com/mesh)的下載區（本站直連，不用去官網） |
| iPhone / iPad | App Store，需要非中國區 Apple ID（見 [用戶端 06](06-ios-app-store.md)） |

## 登入

1. **先退出官方賬號**（登入過的話）：手機點頭像 → Log Out；電腦執行 `tailscale logout`（Linux 前加 sudo）。不退乾淨，下一步的入口不出現。
2. **把登入指向本站**：
   - 手機：未登入介面右上角「⋯」→ Use custom server（部分版本叫 Use an alternate server），填網站私網頁面給的地址，點 Log in。
   - Windows / Linux：在網站頁面複製那條 `tailscale up --login-server=…` 命令，PowerShell / 終端裡執行。
   - macOS：**按住 Option** 點選單欄圖示 → Debug → Custom Login Server → Add Account，填地址。
3. 瀏覽器自動開啟本站登入頁，用本站賬號確認。回到客戶端已經線上。

## 選出口

- 手機：選單 → Exit Node，選一個地區，立即生效。
- 電腦：托盤 / 選單欄圖示 → Exit Node 子選單；或 `tailscale set --exit-node=<地區名>`（`tailscale exit-node list` 看有哪些）。
- 不走出口選 None（命令列等號後留空）。同一時間只能一個出口。

## 到期與裝置數

- 裝置登入有效期跟賬號到期日走，到期幾分鐘內離線；續費後重新點一次登入即可，不用重灌。
- 同時線上臺數按檔位（個人 2 臺、家庭 4 臺、企業 8 臺），與其他接入方式共用額度；同時線上超過檔位上限時，可以臨時升級賬號型別（剩餘時間按價格等值折算），用完之後再切回。

## 別這樣用

- 同一臺裝置上還開著別的 VPN（公司 AnyConnect、其他組網軟體）：會爭 DNS 和路由，看國內影片提示版權、公司內網打不開都是這個原因。
- 校園網 / 公司網限制 UDP：WireGuard 走 UDP，只能靠中繼，很慢；換 AnyConnect。

---
由 [藍盾](https://7d24hrs.com) 團隊整理 · 問題來 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

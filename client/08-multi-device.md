# 08 · 多裝置一次配置、換手機不重來

裝置多的人最煩的是每臺都要配、換了手機又要來一遍、出門在外還得一臺臺點連線。私網把這些都去掉：每臺裝置用本站賬號登入一次就一直線上，重啟、換 Wi‑Fi 都不用管；每臺各選各的出口地區，筆記本走日本、手機走中國區互不影響；同一賬號下的裝置互相能連，筆記本在外面能直接開家裡 NAS 的共享。換新手機直接登入就行。這篇講怎麼把一家的裝置都放進去、額度怎麼算、以及到期和換機的處理。

## 每臺裝置只做一次的事

1. 裝 Tailscale 客戶端（安卓、Windows、macOS、Linux 從本站私網頁面的下載區裝，iPhone / iPad 用 App Store，需要非中國區 Apple ID）。
2. 登入過 Tailscale 官方賬號的先退出，再把登入指向本站的控制伺服器（手機：未登入介面「⋯」→ Use custom server；電腦：複製頁面上那條命令；macOS：Account Settings → Accounts →「Add Account…」旁的箭頭 → Add Account Using Alternate Server）。
3. 瀏覽器裡用本站賬號確認。之後這臺裝置就在私網裡了，不用再碰。
4. 選出口：每臺裝置在自己的選單裡選，各選各的。不走出口選 None，只保留裝置互訪。

## 同時線上臺數怎麼算

一個賬號可以裝在任意多臺裝置上，限制的只是同時線上的數量：個人 2 臺、家庭 4 臺、企業 8 臺，和思科、流量偽裝等其他方式共用同一個額度。同時線上超過檔位上限時，可以臨時升級賬號型別（剩餘時間按價格等值折算），用完之後再切回。

路由器算一臺，它後面的裝置不計數。家裡一臺路由器或 NAS 加上隨身的手機、筆記本，通常就夠。

## 裝置之間互相能連

- 同一賬號下的裝置各有一個私網地址，也能按裝置名互相訪問，不需要公網 IP 和埠對映。
- 筆記本在外面開家裡 NAS 的共享資料夾、手機看家裡的錄影機、給家裡電腦遠端桌面，都用私網地址直連。
- 家裡的路由器裝了本站韌體可以把整個區域網共享進私網，印表機、電視這類裝不了客戶端的裝置也能從外面訪問。
- 其他顧客的裝置在你的私網裡根本不出現，不只是看不到。

## 到期、換機、解除安裝

- 賬號到期：所有裝置幾分鐘內離線，續費後各自重新點一次登入即可，出口設定保留。
- 換手機：新手機按上面步驟直接登入；若提示達到上限，在舊手機上退出登入，或臨時升級賬號型別、用完再切回。
- 不想讓某臺裝置留在私網裡：在客戶端退出登入即可；要強制某臺下線找客服。
- 同一臺裝置上別同時開另一個 VPN（公司的思科、別的組網軟體），會搶 DNS 和路由。

## 常見問題

**每臺裝置可以選不同的出口地區嗎？** 可以，出口是每臺裝置各自選的。筆記本走日本看影片、手機走中國區登網銀，互不影響。

**私網一直開著耗電嗎？** 不選出口時幾乎沒有流量，只有和私網內裝置通訊時才用；電量開銷和系統 VPN 相當。

**家裡 NAS 上怎麼裝？** 群暉、威聯通有 Tailscale 套件，Linux 系統用官方安裝指令碼；登入時同樣指向本站的控制伺服器。裝了本站韌體的路由器不用裝，登入賬號就在私網裡。

**為什麼不用思科在每臺上配？** 也可以，但思科每次要點連線、掉線要重連、換出口要換地址；裝置多的話私網省事得多。校園網限 UDP 的裝置例外，那臺用思科。

## 延伸閱讀

- [私網頁：下載與登入步驟](https://www.leotun.com/zh-TW/mesh?utm_source=github&utm_content=client-08)
- [私網（Tailscale）是什麼](https://www.leotun.com/zh-TW/guides/tailscale-mesh?utm_source=github&utm_content=client-08)
- [在國外看國內家裡的監控和 NAS](https://www.leotun.com/zh-TW/guides/home-camera?utm_source=github&utm_content=client-08)
- [路由器韌體能做什麼](https://www.leotun.com/zh-TW/guides/router-firmware?utm_source=github&utm_content=client-08)

本文網站版（含繁體與英文）：https://www.leotun.com/zh-TW/guides/multi-device?utm_source=github&utm_content=client-08

---
由 [雷騰](https://www.leotun.com/zh-TW?utm_source=github&utm_content=client-08) 團隊整理 · 問題來 [聯絡頁面](https://www.leotun.com/zh-TW/contact?utm_source=github&utm_content=client-08)（群組、郵件、客服都在上面） · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

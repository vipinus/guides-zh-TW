# 雷頓知識庫

> 2026-10-05 起中文名由「藍盾」改為「雷頓」（英文名 LeoTun 不變），同一家、同一個團隊，賬號與服務都不變。

跨境訪問的原理、場景、客戶端設定、路由器與排障，一篇講一件事，不堆術語。由 [雷頓](https://7d24hrs.com/zh-TW?utm_source=github&utm_content=readme) 團隊維護。

其他語言：[简体中文](https://github.com/vipinus/guides-zh-CN) · [English](https://github.com/vipinus/guides-en)

## 長期福利：免費時長，一直有效

| 怎麼領 | 得到什麼 |
|---|---|
| 註冊後領免費試用 | 24 小時全功能試用，不要信用卡 |
| 邀請朋友註冊並首次付費 | 你的有效期 +30 天（家庭檔 +15 天、企業檔 +7.5 天），每位朋友一次，人數不限 |

網站：<https://7d24hrs.com/zh-TW?utm_source=github&utm_content=readme> · 聯絡我們：<https://7d24hrs.com/zh-TW/contact?utm_source=github&utm_content=readme>

## 目錄

### [回國訪問指南 · 需要中國 IP 的那些事](china-access/)

人在海外，很多國內服務會因為你的 IP 不在中國大陸而拒絕：影片、音樂、政務、銀行、購票、遊戲。一篇一個場景，講清楚**為什麼被攔、怎麼解決、還有什麼坑**。

| 篇 |
|---|
| [01 · 哪些服務需要中國 IP](china-access/01-what-needs-a-china-ip.md) |
| [02 · 在國外看國內影片](china-access/02-watch-chinese-video-abroad.md) |
| [03 · 上國內政府與公共服務網站](china-access/03-government-and-public-services.md) |
| [04 · 網銀、手機銀行與支付](china-access/04-banking-and-payments.md) |
| [05 · 音樂、播客與有聲書](china-access/05-music-and-audio.md) |
| [06 · 國服遊戲與直播](china-access/06-gaming-and-streaming.md) |
| [07 · 在國外看國內家裡的監控](china-access/07-home-camera-abroad.md) |
| [08 · 回國線路怎麼選：國內 IP 從哪來、免費的坑在哪](china-access/08-how-to-choose-a-china-access-line.md) |
| [09 · 驗證碼收不到與國內手機號](china-access/09-sms-code-and-china-phone-number.md) |
| [10 · 留學生回國 VPN 怎麼配](china-access/10-students.md) |
| [11 · 回國 VPN 免費還是付費](china-access/11-free-vs-paid.md) |
| [12 · 出差旅行怎麼配](china-access/12-travel.md) |
| [13 · 微信、支付寶與國內小程式](china-access/13-wechat-alipay-miniprograms.md) |
| [14 · 幫國外的長輩設定：裝一次，之後不用管](china-access/14-help-parents-abroad.md) |
| [15 · 網課、考試報名與學歷認證](china-access/15-online-courses-and-exams.md) |

### [出海訪問指南 · 在國內用海外服務](overseas-access/)

人在國內，辦公、開發、學術、遊戲、影音要用的海外服務打不開或者極慢。一篇一個場景，講清楚**要什麼、怎麼選、有什麼坑**。

| 篇 |
|---|
| [01 · 哪些服務需要海外 IP，線路是怎麼工作的](overseas-access/01-what-needs-an-overseas-ip.md) |
| [02 · 思科 AnyConnect 在中國能用嗎](overseas-access/02-anyconnect-in-china.md) |
| [03 · 在國內選哪個地區最快：按運營商](overseas-access/03-which-region-is-fastest.md) |
| [04 · 公司電腦怎麼用：沒有管理員許可權、已連著公司 VPN](overseas-access/04-office-laptop.md) |
| [05 · Linux 伺服器和命令列工具怎麼走線路](overseas-access/05-linux-server.md) |
| [06 · 群暉、威聯通 NAS 怎麼走線路](overseas-access/06-nas-openvpn.md) |
| [07 · 訪問 AI 工具（ChatGPT、Claude、Gemini 等）](overseas-access/07-ai-tools.md) |
| [08 · 查文獻、下論文、投稿](overseas-access/08-academic-research.md) |

### [網路知識筆記 · Network Guides](network/)

講清楚跨境訪問的**原理**、**六種接入方式怎麼選**、我們和別家的區別、怎麼識別有風險的軟體。不堆術語。

| 篇 |
|---|
| [01 · 回國訪問是怎麼回事](network/01-why-china-services-block-overseas.md) |
| [02 · 各種連線方式適用的場景](network/02-choose-your-connection-method.md) |
| [03 · 私網（Tailscale）和 VPN 的區別，什麼時候該用它](network/03-private-network-vs-vpn.md) |
| [04 · 我們和其他 VPN 的區別](network/04-why-us.md) |
| [05 · 如何識別有風險的 VPN 軟體](network/05-risky-vpn-apps.md) |
| [06 · 為什麼有時候快、有時候慢](network/06-why-sometimes-fast-sometimes-slow.md) |
| [07 · 哪些問題靠線路解決，哪些要另找辦法](network/07-when-you-do-not-need-us.md) |
| [08 · 賬號三檔怎麼選、續費與付款](network/08-account-tiers-and-payment.md) |
| [09 · 連線不夠裝置用怎麼辦](network/09-not-enough-devices.md) |

### [客戶端安裝與設定 · Client Guides](client/)

把每種接入方式**裝起來、連上**的一步步說明：思科 AnyConnect、Hiddify、網頁代理擴充套件、OpenVPN、私網 Tailscale，以及 iOS 裝不了應用、Telegram / Discord 安裝、多裝置一次配置、Dropbox 等軟體要填代理怎麼辦。選哪種見 [各種連線方式適用的場景](network/02-choose-your-connection-method.md)，裝好了連不上見 [排障](troubleshooting/)。

| 篇 |
|---|
| [01 · 思科 AnyConnect：各平臺安裝、連線與更新](client/01-anyconnect-install.md) |
| [02 · Hiddify 訂閱連結、匯入連結、分享連結是什麼，要不要"訂閱轉換"](client/02-singbox-subscription-links.md) |
| [03 · 網頁代理：ZeroOmega 擴充套件兩步配好](client/03-web-proxy-extension.md) |
| [04 · OpenVPN：下載 .ovpn 配置匯入即連，路由器、NAS、Linux 都能用](client/04-openvpn-profile.md) |
| [05 · 私網（Tailscale）：安裝、登入本站控制伺服器、選出口](client/05-tailscale-private-network.md) |
| [06 · iOS 裝不了應用怎麼辦](client/06-ios-app-store.md) |
| [07 · Telegram 與 Discord 的安裝](client/07-install-telegram-discord.md) |
| [08 · 多裝置一次配置、換手機不重來](client/08-multi-device.md) |
| [09 · 偽裝（Hiddify）各平臺安裝：Windows、macOS、Linux、安卓、iOS](client/09-hiddify-install-all-platforms.md) |
| [10 · Dropbox 等軟體要填 HTTP / SOCKS 代理怎麼辦](client/10-app-proxy.md) |

### [路由器與家庭網路指南](router/)

整個家的裝置一起走線路：預裝路由器上手、自己刷韌體、分流原理、電視與老人、繫結與換機。

| 篇 |
|---|
| [01 · 預裝路由器怎麼開始](router/01-plug-and-play-router.md) |
| [02 · 自己刷韌體：從官方韌體一步步照著做（附影片）](router/02-flash-firmware-yourself.md) |
| [03 · 路由器分流是什麼](router/03-router-split-routing.md) |
| [04 · 給家裡老人和電視用](router/04-family-tv-and-router.md) |
| [05 · MAC 繫結與換路由器](router/05-mac-binding-and-replacing.md) |
| [06 · 在國外用路由器解鎖國內影片網站](router/06-unlock-chinese-video-with-router.md) |
| [07 · 該不該上路由器，四個型號怎麼挑](router/07-which-router-to-buy.md) |
| [08 · 韌體裝好之後：會自己做的事，和你要知道的幾個開關](router/08-what-the-firmware-does.md) |
| [09 · 路由器真分流和假分流有什麼區別](router/09-real-vs-fake-split.md) |
| [10 · 路由器後面的 NAS、印表機、攝像頭會受影響嗎](router/10-nas-printer-camera-behind-router.md) |
| [11 · 千兆、2G 寬頻配路由器，速度由什麼決定](router/11-fast-broadband-and-router-speed.md) |
| [12 · 路由器斷電、斷網之後會自己恢復嗎](router/12-after-power-cut-or-dropout.md) |

### [排障指南](troubleshooting/)

出問題時按順序查的清單：連不上、慢、斷線，開了回國還是不能看，IPv6 與 DNS 漏網，流量偽裝匯入了連不上，最後是怎麼聯絡我們。安裝類內容已歸到 [客戶端指南](client/)。

| 篇 |
|---|
| [01 · 連不上、慢、斷線的排查清單](troubleshooting/01-cannot-connect-slow-drops.md) |
| [02 · 開了回國還是不能看，怎麼辦](troubleshooting/02-still-blocked-after-connecting.md) |
| [03 · 連上了影片站還提示版權：IPv6 和 DNS 是漏網之魚](troubleshooting/03-ipv6-and-dns-leak.md) |
| [04 · 流量偽裝（Hiddify）匯入了卻連不上](troubleshooting/04-singbox-import-not-connecting.md) |
| [05 · 怎麼聯絡我們、怎麼不失聯](troubleshooting/05-how-to-reach-us.md) |
| [06 · Mac 提示「已損壞」怎麼辦](troubleshooting/06-antivirus-false-positive.md) |
| [07 · 換手機、換電腦、重灌系統之後](troubleshooting/07-new-phone-new-computer.md) |
| [08 · 怎麼確認真的連上了、現在從哪個地區出去](troubleshooting/08-am-i-connected.md) |
| [09 · 請客服遠端幫你看電腦和路由器](troubleshooting/09-remote-assist.md) |
| [10 · 如何有效溝通 AI 客服](troubleshooting/10-ask-ai-support.md) |

有問題可以在本倉庫的 [Discussions](https://github.com/vipinus/guides-zh-TW/discussions) 裡提問。

> 本庫由原來的六個倉庫（china-access-guides、overseas-access-guides、network-guides、client-guides、router-guides、troubleshooting-guides）於 2026-10-04 合併而成，文章內容未改。

## 許可

文字內容採用 [CC BY 4.0](LICENSE)，轉載請註明來源並保留連結。

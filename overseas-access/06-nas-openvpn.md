# 06 · 群暉、威聯通 NAS 怎麼走線路

NAS 是家裡最需要走線路又最沒人管的裝置：下載器要連海外資源、Docker 要拉映象、Cloud Sync 要同步海外網盤、Plex 要刮削後設資料。NAS 裝不了 Hiddify，但群暉和威聯通都自帶 OpenVPN 客戶端——在本站專網頁面下載一個 .ovpn，匯入即連，開機自動重連。這篇講群暉和威聯通各自的匯入位置、「使用預設閘道器」這個關鍵選項、改密碼後的處理，以及為什麼「從外面訪問 NAS」是另一件事、要用私網。

## 先分清兩件事

讓 NAS 自己走線路（下載、拉映象、同步海外網盤）：用專網 OpenVPN，本篇講的。

從外面訪問 NAS（出差時開共享、看監控）：用私網 Tailscale，把 NAS 和你的手機放進同一個私有網路，見《在國外看國內家裡的監控和 NAS》。這件事交給私網——專網負責把 NAS 接到我們的線路，私網負責把你接進家裡。

## 群暉 Synology

1. 登入本站，在專網頁面點地區國旗，下載該地區的 .ovpn 檔案。
2. 控制面板 → 網路 → 網路介面 → 新增 → 建立 VPN 配置檔案 → OpenVPN（透過匯入 .ovpn 檔案），填本站賬號郵箱和密碼。
3. 「使用預設閘道器」：勾上，NAS 的所有出站流量走線路（下載、Docker、Cloud Sync 都受益）；不勾，只是建立隧道、出站仍走本地。絕大多數場景要勾。
4. 「伺服器上的連線丟失時重新連線」勾上，NAS 重啟或線路波動後自動恢復。連線，然後到套件裡試一次拉取。

## 威聯通 QNAP

1. 同樣下載 .ovpn。
2. QVPN Service → VPN 客戶端 → 新增 → OpenVPN，匯入檔案，填賬號密碼。
3. 在連線設定裡勾選「使用 VPN 作為 NAS 的預設閘道器」和自動重連，連線。

## 哪些流量會走、哪些不會

- 走：Download Station / Download Station 的 BT 與 HTTP 任務、Docker 拉映象、Cloud Sync 同步 Google Drive / Dropbox / OneDrive、Plex 和 Emby 刮削後設資料、套件中心更新。
- 不走：區域網內你訪問 NAS 的流量——它本來就在局域網裡，不受影響。
- 人在國內想讓國內網站直連：NAS 上沒有分流指令碼，專網連上後 NAS 的全部出站走線路；國內下載源慢的話，在下載任務裡用國內映象地址，或者只在需要時連線路。

## 要知道的

- 配置檔案裡帶著你的賬號，NAS 上的密碼欄位改密碼後會失效：重新下載 .ovpn 替換，或者只改 VPN 配置裡的密碼。
- 賬號到期 NAS 會斷線，續費後自動重連，配置不用換。
- NAS 算一臺裝置，與其他裝置共用同時線上額度（個人 2 臺、家庭 4 臺、企業 8 臺）。
- 線路走 UDP；NAS 放在家裡寬頻下幾乎不會遇到限 UDP 的問題。

## 常見問題

**勾了「使用預設閘道器」後區域網還能訪問 NAS 嗎？** 能。區域網流量不經過閘道器，共享、Plex 播放、管理頁都不受影響。

**NAS 走線路後 Plex 遠端播放變慢？** Plex 的遠端播放走 NAS 的出站，勾了預設閘道器後會經線路繞一圈。要遠端播放的話，用私網訪問 NAS 更直接；或者只在需要下載時連專網。

**能只讓 Download Station 走線路嗎？** 群暉和威聯通沒有按應用分流。要精細控制，在 Docker 裡跑一個帶 OpenVPN 的下載容器（如 qbittorrent + gluetun）只讓它走線路。

**Linux 系統的 NAS（TrueNAS、Unraid）怎麼辦？** 按 Linux 的方式：openvpn 包 + 配置檔案放到 /etc/openvpn/client/，見《Linux 伺服器和命令列工具怎麼走線路》。

## 延伸閱讀

- [專網頁：客戶端下載與配置檔案](https://www.leotun.com/zh-TW/openvpn?utm_source=github&utm_content=overseas-access-06)
- [OpenVPN 怎麼用、什麼時候選它](https://www.leotun.com/zh-TW/guides/openvpn-setup?utm_source=github&utm_content=overseas-access-06)
- [在國外看國內家裡的監控和 NAS](https://www.leotun.com/zh-TW/guides/home-camera?utm_source=github&utm_content=overseas-access-06)
- [Linux 伺服器和命令列工具怎麼走線路](https://www.leotun.com/zh-TW/guides/linux-server?utm_source=github&utm_content=overseas-access-06)

本文網站版（含繁體與英文）：https://www.leotun.com/zh-TW/guides/nas-openvpn?utm_source=github&utm_content=overseas-access-06

---
由 [雷頓](https://www.leotun.com/zh-TW?utm_source=github&utm_content=overseas-access-06) 團隊整理 · 問題來 [聯絡頁面](https://www.leotun.com/zh-TW/contact?utm_source=github&utm_content=overseas-access-06)（群組、郵件、客服都在上面） · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

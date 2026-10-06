# 04 · OpenVPN：下載 .ovpn 配置匯入即連，路由器、NAS、Linux 都能用

> 網站版（更長、含繁體與英文）：https://7d24hrs.com/zh-TW/guides/openvpn-setup

OpenVPN 是老牌開源協議，幾乎所有系統、路由器韌體、NAS 都自帶客戶端。雷頓的配置檔案已經帶好賬號密碼和加密材料，匯入就能連。手機電腦日常用 AnyConnect 或 Hiddify 更省事；OpenVPN 的價值在**只認 OpenVPN 的地方**：OpenWrt 路由器、群暉 / 威聯通 NAS、Linux 伺服器、老裝置。

## 三步

1. 在[網站專網頁面](https://7d24hrs.com/openvpn)的表裡裝你係統的客戶端（各平臺都有官方 OpenVPN Connect；Windows 也可用 OpenVPN GUI，macOS 可用 Tunnelblick）。
2. 登入後**點地區國旗**下載該地區的 .ovpn。一個地區一個檔案。
3. 客戶端裡開啟這個檔案，連線。

| 平臺 | 說明 |
|---|---|
| Windows / macOS / Android / iOS | 配置已內建賬號密碼，匯入即連 |
| Linux | 系統 VPN 設定 → 從檔案匯入，首次連線填網站郵箱與密碼；命令列 `openvpn --config 檔案`；開機自啟放 `/etc/openvpn/client/` |
| OpenWrt 路由器 | 裝 luci-app-openvpn，上傳 .ovpn 啟用；預裝本站韌體的不需要 |
| 群暉 NAS | 控制面板 → 網路 → 網路介面 → 新增 → VPN → OpenVPN（匯入 .ovpn）；要讓 NAS 出站走線路就勾「使用預設閘道器」 |
| 威聯通 NAS | QVPN → VPN 客戶端 → 新增 → OpenVPN，匯入 |

## 國內使用者：國內網站直連

連上後國內網站會繞遠。網站提供「國內直連工具」，雙擊執行，國內 IP 直連、其餘走線路，思科和專網通用。海外使用者別用它。

## 連不上按順序查

| 日誌關鍵詞 / 表現 | 原因 | 做法 |
|---|---|---|
| AUTH_FAILED | 賬號密碼錯或到期 | 登入網站看有效期；改過密碼要重新下載配置 |
| 先 UDP 超時，隨後改用 TCP 連上 | 當前網路限制了 UDP，自動走了 TCP 兜底 | 能用但會慢；嫌慢換網路或改用 AnyConnect |
| UDP 和 TCP 都報 TLS handshake failed / key negotiation failed | 到伺服器的網路不通 | 換地區、換網路 |
| 匯入報錯 | 客戶端太舊（OpenVPN 2.5 以前） | 更新客戶端 |
| 連著突然斷 | 賬號到期，伺服器斷開 | 續費後重連，配置不用換 |

## 走 UDP 還是 TCP

兩種都有，不用自己選。配置裡 UDP 排在前面，客戶端先試 UDP；UDP 被限或連不上時，幾秒後自動改走 TCP。UDP 延遲低、速度快；TCP 只是保底，跨境會明顯變慢。常年限制 UDP 的網路（部分校園網、公司網）建議直接用 AnyConnect。

> 2026 年 9 月 15 日以前下載的配置只有 UDP，想要自動切換請重新下載。

## 安全

配置檔案裡帶賬號密碼，等於賬號本身，別外傳；洩露了在網站改密碼，舊檔案立刻失效。線路的握手本身也加了密，沒有配置裡的金鑰連握手都發不起，伺服器對掃描器不可見。

---
由 [雷頓](https://7d24hrs.com) 團隊整理 · 問題來 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

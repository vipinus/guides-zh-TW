# 05 · Linux 伺服器和命令列工具怎麼走線路

Linux 上走線路有兩條路，按需求選：整臺機器都走（拉 Docker 映象、跑需要海外網路的服務、無人值守）用專網 OpenVPN，一個配置檔案放進 /etc/openvpn/client/ 開機自啟；只讓幾個命令走（git、pip、npm、curl）用網頁代理，把代理地址填進 http_proxy 環境變數，其餘流量不動。桌面 Linux 還可以在網路管理器裡匯入。這篇三種都講，附密碼檔案的寫法和驗證命令。

## 路一：整機走線路（專網 OpenVPN）

1. 裝客戶端：Debian / Ubuntu sudo apt install openvpn，Fedora sudo dnf install openvpn，Arch sudo pacman -S openvpn。
2. 登入本站，在專網頁面點地區國旗下載 .ovpn。Linux 拿到的配置不內建賬號密碼（網路管理器不接受內建賬密的檔案），所以另建一個密碼檔案：兩行，第一行本站郵箱，第二行密碼，chmod 600。
3. 把 .ovpn 複製為 /etc/openvpn/client/<地區>.conf，在檔案裡的 auth-user-pass 後面加上密碼檔案的路徑。
4. sudo systemctl enable --now openvpn-client@<地區>。看狀態 systemctl status openvpn-client@<地區>，驗證 curl -s https://ipinfo.io/country 顯示的是你選的地區。
5. 換地區就再下一份配置、再啟用一個單元；同時只跑一個。

## 路二：只讓命令列工具走（網頁代理）

本站網頁代理頁面給的代理地址和你的賬號密碼，可以直接填進環境變數：export https_proxy=https://使用者名稱:密碼@代理地址 export http_proxy=$https_proxy。密碼裡有特殊字元要 URL 編碼。之後 curl、wget、git、pip、npm 在這個終端裡都走線路，其他程式不受影響。

Docker 守護程序不讀 shell 環境變數，要寫進 /etc/systemd/system/docker.service.d/proxy.conf 的 Environment= 再重啟 docker；apt 寫 /etc/apt/apt.conf.d/proxy.conf 的 Acquire::https::Proxy。

這條路不掉線、不需要 root、不改路由，適合公司伺服器和只想加速拉取的場景；代價是隻覆蓋認代理變數的程式。

## 路三：桌面 Linux 用網路管理器

1. 裝 network-manager-openvpn-gnome（本站專網頁面點一下可喚起軟體中心）。
2. 設定 → 網路 → VPN → 「+」→ 從檔案匯入，選 .ovpn，填本站郵箱和密碼，儲存。
3. 頂欄或托盤裡開關 VPN。要開機自動連，在有線/無線連線的設定裡勾「自動連線到 VPN」。

## 驗證與排查

- 看出口：curl -s https://ipinfo.io 的 country 是你選的地區。
- 看 DNS：resolvectl status 裡 VPN 介面的 DNS 應是線路下發的；洩露的話在配置里加 dhcp-option DNS 或用 update-systemd-resolved 指令碼。
- AUTH_FAILED：密碼檔案寫錯或賬號到期；改過密碼要更新密碼檔案。
- TLS handshake timeout：到伺服器的 UDP 不通，換地區或換網路；雲伺服器的安全組要放行出站 UDP。
- 伺服器在國內、要國內源直連：專網連上後全部出站走線路，把 apt / pip / npm 的源改成國內映象，或改用路二隻讓特定命令走。

## 要知道的

- 一臺 Linux 算一臺裝置，與其他裝置共用同時線上額度（個人 2 臺、家庭 4 臺、企業 8 臺）；路二的網頁代理按連線計，也算在內。
- 配置檔案和密碼檔案等於你的賬號，別提交進 git 倉庫、別放進映象。
- 改密碼後舊配置立刻失效，這是設計上的吊銷手段；更新密碼檔案即可。
- 雲伺服器上跑線路請遵守服務商的使用條款；線路只記錄連線時長和流量總量。

## 常見問題

**為什麼 Linux 的配置不內建賬號密碼？** 網路管理器匯入配置時不接受內建賬密的檔案，會報匯入失敗，所以發給 Linux 的那份讓你自己填；用 systemd 方式就寫進密碼檔案。

**能只讓 Docker 走線路嗎？** 能，給 Docker 守護程序單獨配代理變數（路二）；或者跑一個帶 OpenVPN 的容器（gluetun）讓特定容器走線路。

**私網 Tailscale 在 Linux 上呢？** 官方指令碼一行安裝，tailscale up --login-server=<本站控制伺服器> 登入，適合要從外面訪問這臺機器、或者要一次配置永遠線上的場景；只是拉取加速用專網或代理更簡單。

**路由器上的 OpenWrt 也這樣嗎？** OpenWrt 裝 luci-app-openvpn 上傳 .ovpn 即可，整個區域網走線路；裝了本站韌體的路由器不需要，登入賬號就行。

## 延伸閱讀

- [專網頁：客戶端下載與配置檔案](https://7d24hrs.com/zh-TW/openvpn)
- [OpenVPN 怎麼用、什麼時候選它](https://7d24hrs.com/zh-TW/guides/openvpn-setup)
- [群暉、威聯通 NAS 怎麼走線路](https://7d24hrs.com/zh-TW/guides/nas-openvpn)
- [網頁代理是什麼、什麼時候用](https://7d24hrs.com/zh-TW/guides/web-proxy)

本文網站版（含繁體與英文）：https://7d24hrs.com/zh-TW/guides/linux-server

---
由 [雷頓](https://7d24hrs.com) 團隊整理 · 問題來 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

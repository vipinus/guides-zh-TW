# 04 · 公司電腦怎麼用：沒有管理員許可權、已連著公司 VPN

公司電腦有三個限制：裝不了未審批的軟體、沒有管理員許可權、經常已經連著公司 VPN。整機 VPN 在這裡要麼裝不上，要麼和公司 VPN 打架。合適的工具是網頁代理——一個瀏覽器擴充套件，只讓這個瀏覽器的請求走線路，公司內網、郵件客戶端、公司 VPN 全都原地不動，也不需要管理員許可權。這篇講怎麼配、能做什麼、什麼別做，以及怎麼和公司的 IT 政策相處。

## 為什麼是網頁代理

- 不裝客戶端：只是一個瀏覽器擴充套件，多數公司允許裝擴充套件但不允許裝軟體。
- 不要管理員許可權：擴充套件在使用者態執行，不改系統網路設定。
- 和公司 VPN 並存：公司 VPN 接管的是系統路由，網頁代理只在瀏覽器這一層，兩者互不干擾；公司內網頁面繼續走公司 VPN。
- 從理論上就不存在掉線：代理按請求走，沒有長連線，公司網路抖動也感覺不到。

## 兩步配好

1. 瀏覽器裝 ZeroOmega 擴充套件（SwitchyOmega 的延續版本），本站網頁代理頁面有各瀏覽器的安裝入口。
2. 登入本站，在網頁代理頁面點「複製外掛恢復地址」，到擴充套件的「匯入/匯出」→「從線上恢復」貼上。地區和地址一次匯入，之後點擴充套件圖示選地區，瀏覽器彈的登入框填本站賬號密碼。
3. 建議單獨開一個瀏覽器配置檔案（或另一個瀏覽器）專門走代理，工作瀏覽器保持本地，兩邊不混。

## 適合做什麼、哪些場景換一種方式

- 能：查資料、開 Google、GitHub、Stack Overflow、海外文件站、ChatGPT 網頁版、網頁版郵箱。
- 換一種方式：影片 App、桌面軟體、命令列工具預設不走瀏覽器的代理設定（命令列可以把代理地址填進 http_proxy 環境變數，見 Linux 那篇）。
- 換一種方式：看國內影片站（海外使用者）——影片站還查 IPv6 和 DNS，網頁代理管不到；那個場景要整機 VPN。

## 和 IT 政策相處

公司電腦上的一切都可能被公司審計，擴充套件也不例外。先看公司的可接受使用政策：多數公司禁止的是未審批軟體和繞過安全策略，瀏覽器擴充套件訪問外部網站通常在灰色地帶，拿不準就問 IT。

別在公司電腦上裝整機 VPN（思科、私網、流量偽裝）來繞過公司策略：它們改系統路由，會觸發終端管理軟體的告警，也會把公司內網流量帶出去。網頁代理隻影響一個瀏覽器，風險最小。

工作賬號和私人賬號分開：走代理的瀏覽器裡別登入公司賬號，公司瀏覽器裡別登入私人賬號。

## 常見問題

**公司禁止裝擴充套件怎麼辦？** 那就用自己的手機或私人電腦。別用來路不明的便攜版軟體繞過管控。

**擴充套件會看到我公司內網的流量嗎？** 不會。分流規則下公司內網域名走直連，不經過代理；用全域性模式時它們也只是被送到代理伺服器再回來，代理看到的是域名不是內容。穩妥起見給代理單獨一個瀏覽器配置檔案。

**公司 VPN 開著時代理還能用嗎？** 能，兩者不衝突。極少數公司 VPN 會強制所有流量走公司出口並停用代理設定，那種情況下擴充套件會報連不上，只能關公司 VPN。

**Mac 的公司電腦也一樣嗎？** 一樣，Chrome、Edge、Firefox 的擴充套件都有 Mac 版。Safari 沒有這個擴充套件，換一個瀏覽器。

## 延伸閱讀

- [網頁代理設定頁：擴充套件安裝與恢復地址](https://www.leotun.com/zh-TW/httpproxy?utm_source=github&utm_content=overseas-access-04)
- [網頁代理是什麼、什麼時候用](https://www.leotun.com/zh-TW/guides/web-proxy?utm_source=github&utm_content=overseas-access-04)
- [Linux 伺服器和命令列工具怎麼走線路](https://www.leotun.com/zh-TW/guides/linux-server?utm_source=github&utm_content=overseas-access-04)
- [各種連線方式適用的場景](https://www.leotun.com/zh-TW/guides/choose-connection?utm_source=github&utm_content=overseas-access-04)

本文網站版（含繁體與英文）：https://www.leotun.com/zh-TW/guides/office-laptop?utm_source=github&utm_content=overseas-access-04

---
由 [雷騰](https://www.leotun.com/zh-TW?utm_source=github&utm_content=overseas-access-04) 團隊整理 · 問題來 [聯絡頁面](https://www.leotun.com/zh-TW/contact?utm_source=github&utm_content=overseas-access-04)（群組、郵件、客服都在上面） · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

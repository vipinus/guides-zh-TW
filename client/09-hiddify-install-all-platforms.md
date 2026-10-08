# 09 · 偽裝（Hiddify）各平臺安裝：Windows、macOS、Linux、安卓、iOS

偽裝（流量偽裝）用的客戶端是開源的 Hiddify，自帶 sing-box 核心，裝完不用再配別的。五個平臺用同一個 App，但各平臺裝好之後第一次執行要過的關不一樣：Windows 可能被防毒軟體攔或刪，Mac 可能提示「已損壞」還要給網路擴充套件授權，Linux 要執行一條授權命令才能開 VPN 模式，iPhone 在國區商店搜不到。這篇把每個平臺從哪下載、怎麼裝、第一次執行要做什麼一次講完，最後給匯入訂閱並連上的最短步驟。

## 從哪裡下載

| 平臺 | 安裝包 | 從哪裝 |
|---|---|---|
| Windows | 安裝程式（.exe），只有 x64 | 偽裝頁下載區 |
| macOS | .dmg，Apple 晶片和 Intel 通用一個包 | 偽裝頁下載區 |
| Linux | .deb（Debian / Ubuntu 系），只有 x64 | 偽裝頁下載區 |
| 安卓 | .apk，分 ARM64 和 x86-64 兩個 | 偽裝頁下載區，或 Google Play |
| iPhone / iPad | App Store 的 Hiddify Proxy & VPN | App Store，需要非中國區 Apple ID |

偽裝頁的下載區會按你當前的系統自動推薦對應的包，其他系統的包也列在下面。每一行旁邊還有「官方網站」圖示，指向 Hiddify 官方釋出頁，可以對照版本。桌面三個系統（Windows、macOS、Linux）還有影片教程。

桌面安裝包是 Hiddify 官方釋出包的原樣映象，不改動、不重新打包。放行之前可以先自己核對：把安裝包上傳 VirusTotal 看看，方法見 [排障 06](../troubleshooting/06-antivirus-false-positive.md)。

## Windows

1. 從偽裝頁下載區下載安裝程式，雙擊安裝。（目前實測 Windows 安全中心不會報毒；萬一你裝的防毒軟體報了，見 [排障 06](../troubleshooting/06-antivirus-false-positive.md) 最後的常見問題。）

## macOS

1. 從偽裝頁下載區下載 .dmg，開啟後把 Hiddify 拖進「應用程式」。
2. 在「訪達」→「應用程式」裡按住 Control 點 Hiddify 圖示，選「開啟」，在對話方塊裡再點一次「開啟」。
3. 還是打不開：「系統設定」→「隱私與安全性」，在「安全性」一欄點「仍要開啟」，輸入密碼確認。
4. 提示「已損壞，無法開啟」：檔案並沒有壞，是系統的 Gatekeeper 在攔截。開啟「終端」，執行下面這條命令，回車後輸入登入密碼，再開啟 Hiddify：

```bash
sudo xattr -dr com.apple.quarantine /Applications/Hiddify.app
```

這條命令只移除下載來源的隔離標記，只對這一個 App 生效。**不要**用 `sudo spctl --master-disable` 整機關掉 Gatekeeper。

裝好後第一次點連線，系統還會要求給「網路擴充套件」授權，不做這步圖示會一直轉圈、連不上：

- **macOS 15 Sequoia 及更新**：「系統設定」→「通用」→「登入項與擴充套件」，拉到底部的「擴充套件」，顯示方式切成「按類別」，點「網路擴充套件」旁邊的 ⓘ，開啟 Hiddify 的開關，按提示輸入密碼或驗證指紋。
- **macOS 13 Ventura / 14 Sonoma**：先啟動 Hiddify 並點一次連線，會彈出「系統擴充套件已被阻止」；然後「系統設定」→「隱私與安全性」，往下找到「來自開發者 … 的系統軟體已被阻止載入」，點「允許」並輸入密碼。

公司配發的 Mac 如果這些按鈕是灰的，是裝置管理策略鎖住了，找 IT，或者改用思科、專網、私網客戶端。

## Linux

1. 從偽裝頁下載區下載 .deb，雙擊用軟體中心安裝，或在下載目錄開啟終端執行（Debian、Ubuntu 及其衍生版）：

```bash
sudo apt install ./下載的檔名.deb
```

2. 裝完直接連線會報「operation not permitted」，開不了 VPN 模式——官方 deb 裝好後沒有這項許可權。開啟終端執行下面這條命令給 Hiddify 授權，然後重新開啟 Hiddify：

```bash
echo /usr/share/hiddify/lib | sudo tee /etc/ld.so.conf.d/hiddify.conf && sudo ldconfig && sudo setcap cap_net_admin,cap_net_raw+ep /usr/share/hiddify/hiddify
```

3. **每次升級 Hiddify 後要再執行一次**：授權掛在程式檔案上，升級換了檔案，授權就沒了。

deb 包是 x64 的；ARM 的 Linux 裝置用專網（OpenVPN），賬號通用。

## 安卓

1. 從偽裝頁下載區下載 .apk。頁面會按你的手機自動推薦架構，絕大多數手機是 ARM64。能用 Google Play 的也可以直接在商店裝。
2. 安裝時提示「未知來源」或安全軟體提醒，允許即可。
3. 第一次點連線時系統會申請 VPN 許可權，點允許。

## iPhone / iPad

1. 在 App Store 搜「Hiddify」安裝，免費。
2. 搜不到、或提示「此專案在您所在的國家或地區不可用」：iOS 從 App Store 安裝，需要非中國區 Apple ID（美國、香港、臺灣、日本、新加坡的商店都有 Hiddify）。推薦新註冊一個：在 App Store 裡對任意免費應用點「獲取」→「建立新 Apple ID」，地區選香港、美國等，付款方式選「無」。只在 App Store 裡切換賬號，不影響 iCloud。完整步驟見 [06 · iOS 裝不了應用怎麼辦](06-ios-app-store.md)。
3. 第一次點連線時系統會申請 VPN 許可權，點允許。

**不要**用別人分享的 Apple ID，對方能遠端鎖你的裝置。

## 裝好後：匯入訂閱並連線

1. 登入網站，開啟偽裝頁。
2. 點想用的地區國旗，彈出二維碼；或點頁面上方的「匯入所有自動選擇」，一次匯入境外全部地區、由客戶端自動選。**中國區單獨匯入**：回國看影片、登網銀時點中國國旗匯入。
3. 手機：點「複製匯入連結」後切到 Hiddify 按提示新增，或用另一臺裝置上的 Hiddify 掃碼。電腦：點「複製配置地址（貼上用）」，在 Hiddify 裡點「+」→「從剪貼簿新增」。
4. 點連線。

三種連結的區別、其他客戶端怎麼匯入、訂閱會不會過期，見 [02 · Hiddify 訂閱連結](02-singbox-subscription-links.md)。匯入了連不上，見 [排障 04](../troubleshooting/04-singbox-import-not-connecting.md)。

## 常見問題

**安裝包是你們改過的嗎？** 不是。桌面安裝包是 Hiddify 官方釋出包的原樣映象，偽裝頁每一行都有指向官方釋出頁的連結，可以自己對照版本，也可以上傳 VirusTotal 複核。


**Mac 上已經執行了 xattr 命令，還是連不上？** 多半是「網路擴充套件」沒授權，按上面 macOS 那一節去系統設定裡開啟 Hiddify 的開關。

**Linux 升級 Hiddify 後又開不了 VPN 模式了？** 正常現象，升級後重新執行一次授權命令。

**ARM 的 Windows 或 Linux 電腦能用嗎？** 能，用專網（OpenVPN）等其他接入方式，賬號通用；Hiddify 桌面包目前是 x64 的。

**不想折騰放行步驟？** 思科（Cisco Secure Client）、專網（OpenVPN Connect）、私網（Tailscale）的客戶端都是雙擊即用，不會被報毒，Mac 上也不會提示「已損壞」，賬號是同一個。

## 延伸閱讀

- [偽裝頁：客戶端下載與各地區二維碼](https://www.leotun.com/zh-TW/singbox?utm_source=github&utm_content=client-09)
- [Hiddify 訂閱連結怎麼匯入](https://www.leotun.com/zh-TW/guides/singbox-subscription?utm_source=github&utm_content=client-09)
- [客戶端被報毒 / Mac 提示已損壞：先驗證，再放行](https://www.leotun.com/zh-TW/guides/antivirus-false-positive?utm_source=github&utm_content=client-09)
- [macOS「網路擴充套件」授權是什麼、怎麼放行](https://www.leotun.com/zh-TW/guides/macos-network-extension?utm_source=github&utm_content=client-09)
- [iOS 裝不了應用怎麼辦](https://www.leotun.com/zh-TW/guides/ios-app-store?utm_source=github&utm_content=client-09)

---
由 [雷頓](https://www.leotun.com/zh-TW?utm_source=github&utm_content=client-09) 團隊整理 · 問題來 [聯絡頁面](https://www.leotun.com/zh-TW/contact?utm_source=github&utm_content=client-09)（群組、郵件、客服都在上面） · 註冊領 24 小時免費試用，邀請朋友每位送 30 天，長期有效

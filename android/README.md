# 吞嚥照護本 (SwallowCare) - Android App 專案

本目錄為「**吞嚥照護本**」的完整 Android 原生專案（WebView 封裝版），已將所有介面與功能資源離線內建在 App 內部，無須架設伺服器即可直接離線運行。

---

## 📱 專案特色

1. **完全離線運行**：所有 HTML/CSS/JS/圖片資源打包於 `app/src/main/assets/www` 內。
2. **全螢幕原生沉浸式體驗**：自動隱藏展示邊框與劉海，符合 Android 狀態列與手勢操作。
3. **支援拍照與圖片上傳**：內建 `WebChromeClient` 檔案選擇器與權限配置，支援拍照紀錄餐點與安心錄。
4. **Android 返回鍵支援**：按實體/手勢返回鍵時，優先返回上一層畫面，避免直接退出 App。
5. **硬體加速與快取**：開啟硬體加速與 DOM Storage，滑動流暢不卡頓。

---

## 🚀 如何在 Android Studio 中開啟與編譯 APK

### 步驟 1：開啟 Android Studio
1. 開啟 **Android Studio**。
2. 點擊 **File** -> **Open...**（或在歡迎畫面點擊 **Open**）。
3. 選擇此專案的 `android` 目錄（即 `/home/ming/pinyen_ui/android`）。
4. 等待 Android Studio 完成 Gradle 專案同步（Sync Project with Gradle Files）。

---

### 步驟 2：連接手機或啟動模擬器
- **實體 Android 手機**：
  1. 在手機上開啟「**開發人員選項**」並啟用「**USB 偵錯**」。
  2. 使用傳輸線將手機連接至電腦，手機跳出「允許 USB 偵錯嗎？」時點擊「確定」。
- **或使用 Android Studio 模擬器 (AVD)**：
  1. 點擊工具列的 **Device Manager**。
  2. 建立或啟動任一 Android 虛擬機（建議 Android 10+ / API 29+）。

---

### 步驟 3：執行與安裝 App
1. 點擊 Android Studio 右上角的綠色三角形 **Run 'app'** 按鈕（快捷鍵：`Shift + F10`）。
2. Android Studio 會自動編譯並將 App 安裝到您的手機/模擬器上開啟。

---

### 步驟 4：打包生成 APK 檔案 (匯出給其他人安裝)
如果您想產生 `.apk` 檔案直接傳給家人或測試人員安裝：
1. 在 Android Studio 頂部選單點擊 **Build** -> **Build Bundle(s) / APK(s)** -> **Build APK(s)**。
2. 編譯完成後，右下角會出現提示視窗，點擊 **locate** 即可找到產生的 `app-debug.apk`。
3. 將該 `.apk` 檔案傳送至 Android 手機點擊即可直接安裝！

---

## 📂 專案架構說明

```
android/
├── app/
│   ├── build.gradle                 # App 模組設定 (SDK 版本、依賴項)
│   └── src/
│       └── main/
│           ├── AndroidManifest.xml  # App 權限與 Activity 宣告
│           ├── assets/
│           │   └── www/             # 打包進 App 的網頁前端資源 (index.html)
│           ├── java/com/ansimjia/swallowcare/
│           │   └── MainActivity.java # WebView 容器核心邏輯
│           └── res/
│               ├── layout/          # 主畫面 Layout (WebView + ProgressBar)
│               ├── values/          # 顏色、字串、主題樣式
│               └── drawable/        # App 圖標與向量資源
├── build.gradle                     # 專案級 Gradle 設定
├── settings.gradle                  # 專案模組設定
└── README.md                        # 本說明文件
```

---

## 🛠️ 常見問題 (FAQ)

### Q: 修改了 `index.html` 網頁內容，如何同步到 Android App？
將更新後的 `index.html` 複製覆蓋至 `android/app/src/main/assets/www/index.html`，然後在 Android Studio 重新點擊 **Run** 即可。

### Q: 影片播放無法載入？
示範影片使用的是 YouTube 內嵌播放器，手機需要連上網際網路（Wi-Fi 或行動網路）即可正常觀看示範影片。

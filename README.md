# AI Life Companion 0.4.1

## Android 小晴、動作與聲音精修人工驗收版

# [⬇ 下載 APK](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/AI-Life-Companion-0.4.1.apk)

直接下載、覆蓋安裝並開啟；預設連接既有 HTTPS 雲端，不需要 USB、ADB 或電腦。

- Package：`com.ailifecompanion.app`
- versionName：`0.4.1`；versionCode：`7`
- 大小：127,396,213 bytes（127.40 MB）
- SHA-256：`183399D76ABD3B8AFBC83B5509A3ED27966F016C873C349F4A09329A9047167D`
- 原始碼 commit：`bf1215b4f4de8b523212c4d4f914151cf9e33aae`
- [Cloud Backend health](https://ai-life-companion-api.onrender.com/health)

## 這次改了什麼

保留原生 Filament / glTF 與既有聊天、行走、互動、商城、旅行、相簿、Memory。調整小晴的臉部比例、肩長深棕髮、奶油色上衣及灰綠寬褲；修正頭髮自發光亮帶和貓／房間的網格朝向。走路增加加減速、距離同步步伐及腳底補償，招手加入手腕動作，坐起加入重心過渡。嘴型降低開口幅度並平滑 viseme 切換。

## 最新畫面與影片

[首頁](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/home_refined.png) · [聊天](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/chat_refined.png)

- [walk_refined.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/walk_refined.mp4) — 約 18 秒
- [wave_refined.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/wave_refined.mp4) — 約 18 秒
- [sit_refined.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/sit_refined.mp4) — 約 18 秒
- [expression_refined.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/expression_refined.mp4) — 約 18 秒
- [voice_refined.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/voice_refined.mp4) — 約 40 秒

影片為 Pixel 7a / Android 36 模擬器。同一產品 renderer；語音音軌由同次雲端 TTS 返回並送往 AudioTrack 的 PCM 按時間對齊，不是外部麥克風錄製。未宣稱 Samsung 實測。

## 同句聲音比較

[溫柔](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/voice_gentle.mp3) · [自然](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/voice_natural.mp3) · [成熟](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.1-refined/voice_mature.mp3)

「嗨，今天過得怎麼樣？如果你累了，我可以陪你說說話。」

設定 → 角色聲音可直接試聽與選擇。新增陪伴感；溫柔預設以 0.96 語速、自然台灣中文、連貫語句與句意停頓調校。既有 Realtime、打斷及語音播放流程保留。

## 驗收結果

PASS 指本輪模擬器與工程檢查；尚未完成主觀人工驗收的項目標為 FAIL／待人工，並非以 API 成功代替品質認可。

| 項目 | 結果 |
|---|---|
| Character Likeness | FAIL／辨識度仍待人工確認 |
| Hair Matching | PASS／深棕、肩長、髮尾弧度；瀏海仍風格化 |
| Walk Animation Precision | PASS |
| Wave Animation Precision | PASS |
| Sit/Stand Transition | PASS |
| Idle Naturalness | PASS／模擬器觀察 |
| Facial Expression Clarity | PASS |
| Voice Naturalness | FAIL／待人工試聽 |
| Voice Pleasantness | FAIL／待人工試聽 |
| Lip Sync Quality | PASS／頻譜估計，非精確 phoneme timing |

Android 12 tests × Debug / Release、lint 0 errors、assembleDebug、Backend 13 tests、APK secret scan 通過。公開 Cloud Chat／拿鐵記憶回歸、三組 TTS 及 App 內文字聊天已實測。

公開完整回下載：**PASS**，大小、SHA-256、ZIP CRC、簽章、Package 與版本均一致。

[完整技術說明與限制](README_AVATAR_041.md) · [驗證資料](verification-0.4.1.json)

小晴是 reference-guided 風格化角色，尚非照片本人 3D 重建。服裝非完整幾何替換、髮型無物理模擬；Render Free 可能冷啟動。相似度與聲音偏好請以人工驗收為準。

## 舊版本

[0.4.0 Release](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/tag/v0.4.0-full-body)

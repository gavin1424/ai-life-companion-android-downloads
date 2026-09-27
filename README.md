# AI Life Companion 0.6.0 — HUMAN REVIEW BUILD

## [⬇ 下載 APK](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.6.0-human-review/AI-Life-Companion-0.6.0.apk)

下載 → 安裝 → 開啟 →「跟小晴說話」。使用公開 HTTPS Backend，不需要 USB、ADB 或本機伺服器。進入通話後持續收音，可直接插話；不是每句按一次麥克風。

- Package：`com.ailifecompanion.app`
- versionName：**0.6.0** ／ versionCode：**9**
- APK：**131,852,679 bytes**
- SHA-256：`AA49294204F281F6AFFF38A1DD5E446388D8140B544110281080C1327CA2B553`
- Source commit：`684cc38634d03173cf5290fed0ebcfb61f0d2d17`

## [最終 Android 連續錄影](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.6.0-human-review/android_realtime_avatar_final.mp4)

約 140 秒，最終程式版本、同一 Session，多輪真實 OpenAI 回覆，沒有按角色動作按鈕。這是模擬器受控 PCM 輸入測試；音訊使用同次 AudioTrack PCM 對齊配回，並非 Samsung 真人收音證明。先前 139 秒影片標記 PRE_FINAL。

## 聲音試聽

[A 自然](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.6.0-human-review/Voice-A-Natural.m4a) · [B 溫柔](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.6.0-human-review/Voice-B-Gentle.m4a) · [C 成熟](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.6.0-human-review/Voice-C-Mature.m4a) · [D 陪伴](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.6.0-human-review/Voice-D-Companion.m4a)

同句：「嗨，今天過得怎麼樣？如果有點累，我就在這裡陪你。」App 設定 → 角色聲音可試聽與選擇。

## 驗收範圍

Continuous Idle、Automatic Listen、Automatic Expression、Automatic Gesture、Streaming Speech、Lip Sync Pipeline、Barge-in Pipeline、Conversation Loop：**PASS（受控模擬器工程測試）**。

Sit/Stand、Pet Cat：**EXPERIMENTAL**。素材尚未達品質要求，坐下快捷功能已從小晴首頁隱藏，沒有用假動作冒充。

Samsung Physical Validation、Android VAD Samsung、AEC Samsung、Motion Naturalness、Lip Sync Naturalness、Voice Pleasantness、Character Likeness：**READY_FOR_HUMAN_REVIEW**。

連點設定內 App Version 七次可開 Developer Settings → Realtime Diagnostics，查看 FPS、連線、VAD、角色／語音狀態與打斷次數。

[完整版本說明](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.6.0-human-review/HUMAN_REVIEW_060.md) · [Build manifest](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.6.0-human-review/BUILD_MANIFEST.json)

Build/test/lint、Backend tests、APK secret scan 通過。公開 APK 已重新下載核對大小、SHA-256、版本及簽章。

---

<details>
<summary>歷史版本 0.5.0（非本次驗收版本）</summary>

# AI Life Companion 0.5.0 真人 2D 人工驗收版

## [⬇ 下載 APK](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/AI-Life-Companion-0.5.0.apk?sha=249E80BC3AB3)

正式首頁、聊天、語音通話改用原本小晴真人 identity 的 2D 動態角色。3D 保留於隱藏 Developer / Experimental，預設 OFF。既有雲端與產品資料流程保留。

- Package: `com.ailifecompanion.app`
- versionName: **0.5.0** / versionCode: **8**
- 大小: **124,284,445 bytes / 124.28 MB**
- SHA-256: `249E80BC3AB31A17394B94E0DE21B4734B903593D5D5D8DC36DAC0376FBA21D7`
- Source commit: `1304402b5a11d1e50a71fbc2215b86f7076de7f8`

## 人工驗收

Character Likeness、Realistic Appearance、Natural Movement、Voice Pleasantness 均為 **READY_FOR_HUMAN_REVIEW**。

[首頁](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/home_realistic.png) · [聊天](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/chat_realistic.png) · [Voice Chat](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/voice_chat_realistic.png)

## 動態影片

- [待機 · 01_idle_realistic.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/01_idle_realistic.mp4)
- [眨眼與表情 · 02_blink_expression.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/02_blink_expression.mp4)
- [招手 · 03_wave_realistic.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/03_wave_realistic.mp4)
- [過來一下 · 04_come_closer.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/04_come_closer.mp4)
- [坐下休息 · 05_sit_realistic.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/05_sit_realistic.mp4)
- [說話嘴型 · 06_talking_lipsync.mp4](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/06_talking_lipsync.mp4)

影片為模擬器實際螢幕錄影，約 22–30 秒。語音音軌由同次送往 AudioTrack 的 PCM 按播放時間對齊。Samsung 尚未實測。

## 同句 A / B / C

[A｜自然陪伴](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/voice_A.mp3) · [B｜溫柔](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/voice_B.mp3) · [C｜成熟柔和](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/voice_C.mp3)

「嗨，今天過得怎麼樣？如果有點累，就先休息一下，我陪你聊聊天。」

App 設定 → 角色聲音可直接試聽並選擇。三段實際雲端生成樣本已內建，試聽不用等待連線。

## 技術驗證

Realistic2DAvatarEngine、Identity Consistency technical check、Blink、Expression、Wave、Come Closer、Sit、Lip Sync、Experimental 3D default OFF：PASS。Identity 技術檢查僅驗證來源、臉部輪廓與遮罩，不代替人工判斷相似度。

Android 16 tests × Debug / Release、2 instrumentation tests、Backend 14 tests、lint 0 errors、assembleDebug、APK Secret Scan：PASS。Cloud Chat / memory context、三組 TTS、Realtime 連線回歸通過。

姿勢使用攝影素材交疊過渡，非連續生成影片；交疊可能有短暫重影。Lip sync 為頻譜估計，非精確音素。完整姿勢包本輪專注小晴。

[完整說明](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/README_AVATAR_050.md) · [驗證記錄](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.5.0-realistic-2d/verification-0.5.0.json)

房間已改為單一攝影場景內的人物去背合成，並修正圖片來源改變時的快取刷新。

**公開下載回驗：PASS**。完整檔案 bytes、SHA-256、ZIP CRC、APK 簽章、Package、versionName 與 versionCode 均一致。公開檔案 Secret Scan 亦通過。

[先前 0.4.1 版本](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/tag/v0.4.1-refined)

</details>

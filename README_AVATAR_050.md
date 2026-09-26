# AI Life Companion 0.5.0 — 真人 2D 人工驗收版

Package `com.ailifecompanion.app` · versionName `0.5.0` · versionCode `8`

## 產品路徑

首頁、聊天預覽、語音通話改用 `Realistic2DAvatarEngine` / `Realistic2DAvatarView`。使用原有虛構小晴的真人 reference，不重新設計人物。保留聊天、Memory、商城、旅行、相簿與既有 HTTPS Backend。

0.4.1 的 Filament / glTF、骨骼、行走與互動程式完整保留。設定 → 關於 → App Version 點七次 → Developer Settings → Experimental 3D Avatar；預設 OFF。舊資料庫中的 FULL_BODY 欄位不會使正式首頁自動回到 3D。語音通話固定使用真人 2D。

## Identity Pack

- `assets/realistic2d/manifest.json`：原始 reference 與每項素材的 SHA-256、來源約束、語音樣本。
- 14 組 face rigs 包含 canonical、站姿、招手、坐姿、近景、閉眼、說話及表情來源。使用 ML Kit 實際偵測一張臉、眼／唇／輪廓。
- 預先打包已分析的 landmarks、人物 foreground；建立私有 `files/realistic_identity/050/` 時產生 face crop、左右眼、嘴、臉部、頭髮與上半身 mask。
- 頭髮 mask 為輪廓推導的區域遮罩，與人物 segmentation 相交，**不是獨立的髮絲語義分割模型**。
- bundled selfie segmentation 為人物提供離線遮罩；既有 subject segmentation 仍供寵物／照片流程使用。
- 技術檢查：來源雜湊、單臉、輪廓範圍、相對眼距、透明遮罩及音訊檔完整性。**不代表生物辨識或主觀身份相似度已通過**。

## 真人動畫

圖片只載入一次；快取局部 mesh 權重與頂點陣列，30 FPS 排程。頭部輕轉、眼神、肩部呼吸分區變形，背景不作整張漂浮。

- 眨眼：同一人物的真實閉眼區域，3–7 秒節奏並有 double blink。
- 表情：中性、溫柔笑、開心、害羞、關心、難過、驚訝、思考；輪廓對齊與柔邊過渡。
- 招手：真實抬手 pose + 局部手掌／手腕變形，idle → wave → idle。
- 過來一下：中景 → 平滑交疊 → 原始真人近景。**不是重新做 3D 行走**。
- 坐下：站姿／沙發坐姿交疊過渡；不是物理骨骼坐下模擬。
- 嘴型：同一人物張口照片區域配合 A/E/I/O/U/MBP/FV 頻譜估計，分別控制上唇、下唇、嘴角、下顎。AudioTrack 停止時回休息。**不是精確音素時間戳**。
- 房間：攝影背景 + 人物 foreground、柔和色調、低透明陰影。預設保留照片原有環境；可切換客廳／咖啡廳／海邊等。
- 雪球使用既有真實貓照片的坐姿、抬頭、睡姿、近景、趴著撒嬌，不使用 3D 貓。

完整表情與姿勢包本輪專注小晴。其他使用者新建角色保留自己的照片與局部動態，尚未自動產生與小晴同等的完整姿勢／表情素材包。

## 語音 A / B / C

設定 → 角色聲音：

- A｜自然陪伴
- B｜溫柔
- C｜成熟柔和

同一句：**嗨，今天過得怎麼樣？如果有點累，就先休息一下，我陪你聊聊天。**

三個不同聲線與語氣由已部署的 `/speech` 實際生成，內建 PCM 試聽可立即播放，不需要每次重新付費生成。選擇會保存到角色，後續 TTS 與 Realtime 採用對應 profile。永久 Key 僅在後端，APK 不含 Key。

雲端 Backend：<https://ai-life-companion-api.onrender.com>。Render Free 有冷啟動可能。

## 驗證方式

```powershell
gradlew.bat test
gradlew.bat lint
gradlew.bat assembleDebug
cd backend
npm test
cd ..
python tools/audit_realistic_assets.py
python tools/scan_apk_secrets.py app/build/outputs/apk/debug/app-debug.apk
```

Android 單元測試 16 項 × Debug / Release；新增 Android instrumentation 2 項，驗證實際 Identity Pack、私有裁切／遮罩與寵物照片。原 3D 測試保留。

`RealisticAvatarProofActivity` 僅在 Debug、受 DUMP 權限保護，使用與正式首頁相同 renderer。六段影片為 Pixel 7a / Android 36 模擬器的螢幕錄影：idle、blink/expression、wave、come closer、sit、talking/lipsync。語音影片音軌由**同次實際送往 AudioTrack 的雲端 PCM**按播放時間對齊，非外部麥克風收音。

沒有宣稱 Samsung 已實測。技術 PASS 僅表示流程／動畫／音訊觸發及檔案檢查通過。

## 人工評估

| 項目 | 狀態 |
|---|---|
| Character Likeness | READY_FOR_HUMAN_REVIEW |
| Realistic Appearance | READY_FOR_HUMAN_REVIEW |
| Natural Movement | READY_FOR_HUMAN_REVIEW |
| Voice Pleasantness | READY_FOR_HUMAN_REVIEW |

姿勢 crossfade 中可能短暫看到重影；髮絲去背及嘴型仍為 2D 近似。請以影片及手機人工驗收判斷品質，不以技術通過取代觀感。

## 技術參考

[ML Kit 自拍分割](https://developers.google.com/ml-kit/vision/selfie-segmentation/android) · [OpenAI TTS](https://developers.openai.com/api/docs/guides/text-to-speech) · [OpenAI Realtime voices](https://developers.openai.com/api/docs/guides/realtime-conversations)

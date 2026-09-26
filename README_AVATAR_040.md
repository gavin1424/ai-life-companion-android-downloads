# AI Life Companion 0.4.0 — 全身角色人工驗收版

## 實際引擎

既有 Kotlin / Compose App 保留。主要角色改用原生 Google Filament 1.56 + glTF skinned mesh；Compose 僅承載 TextureView。沒有 WebView、沒有用整張照片的位移代替骨骼動畫。舊照片 renderer 可在角色設定切回。

- humanoid 骨架、手指、關節動畫、房間網格尋路與家具碰撞範圍。
- 原生 GPU skinning；VRM 57 個 facial morph targets；將 sparse accessor 展開，避免載入後表情無效。
- Idle、招手、走路、轉身、走近／走遠、坐下／站起、點頭／搖頭、伸展、害羞、難過、驚訝、笑、睡眠、拍照姿勢、舞蹈。
- 3D 貓使用獨立四足關節控制，可走動、坐下、趴下、擺尾、玩耍。貓與房間為本專案製作。
- 臉部與全身照片保留在本機 Identity Pack；臉部比例與膚色、身體比例用於風格化角色參數。**不是照片到寫實 3D 人像重建**。女性／男性／中性目前共用一個基礎 mesh，改變比例，不代表不同完整造型。
- 服裝為基礎 mesh 的材質配色變化，並非完整的新衣服幾何；房間保持既有資料，新增可導航的 3D 場景。

## 語音與雲端

公開 HTTPS Backend：https://ai-life-companion-api.onrender.com

OpenAI gpt-4o-mini-tts：六個中文聲音設定與試聽，底層 marin / cedar，速度 0.92–0.98。

Realtime：gpt-realtime-2.1，Android AudioRecord → 短期 credential WebSocket → PCM AudioTrack。Server VAD 自動換輪，插話立即清空本機播放佇列並 truncate 已播放項目。永久 OpenAI Key 不進 APK。

嘴型為 PCM 音量、頻譜與過零率估計的 A/E/I/O/U/MBP/FV/Rest，並非精確的語音辨識 phoneme timing。TTS 與 Realtime 使用同一個分析器。修正了 AudioTrack 啟播門檻造成的緩衝死等。

AI Chat 回覆含 text / emotion / avatarAction；後端 JSON schema 與 allowlist 限制動作。已在公開後端實測招手、過來、坐下三種指令。

## 驗證範圍與限制

- `gradlew.bat test`：10 個測試各跑 Debug / Release，包含導航、骨骼姿勢、眨眼、頻譜嘴型、貓動作與 HTTPS 預設。
- `gradlew.bat lint`：0 errors；既有與新增 warnings 列於產生的 lint report。
- `gradlew.bat assembleDebug`、Backend 13 tests、APK secret scan。
- Pixel 7a profile / Android 36 / host GPU 模擬器錄影。**沒有 Samsung 實機 FPS、麥克風、喇叭或人聲自然度的實測結論**。
- 語音影片使用明確的 debug 受控語音輸入，透過真正公開 Backend 取得 session，再直接連 OpenAI Realtime。不是人工麥克風收音的證明。
- Android screenrecord 不錄系統音訊；影片音軌取自同次測試送入／播放的 PCM，依記錄時間對齊。不是另配旁白。手機播放是否好聽仍請人工試聽。
- Render Free 休眠後可能冷啟動；沒有承諾固定數秒回應。每日限額與短期 session 機制保留。
- 基礎 3D 模型為風格化 VRM，不是首頁舊真人照片；相簿與 AI 合照仍使用原有 identity reference。
- 尚未提供貓跳上沙發、完整男性獨立 mesh、頭髮物理或完整服裝 mesh 替換。本版不把這些列為 PASS。

## 素材授權與重建

人體源自 pixiv Inc. 的 VRM1_Constraint_Twist_Sample v1.0.1，依 VRM Public License 1.0 允許修改與再分發。來源、作者、授權旗標與修改項目在 `app/src/main/assets/avatar/avatar-license.json`。未使用公眾人物或名人素材。

1. 下載來源 VRM 至專案外或 ignored 目錄。
2. `python tools/build_avatar_assets.py` 建立房間與貓的原始場景。
3. `python tools/merge_vrm_avatar.py <source.vrm>` 匯入人體、標準化骨架、烘焙 constraint 驅動關係、展開 sparse morphs、壓縮貼圖並保留授權 metadata。
4. App 直接讀取已提交的 GLB，不需使用者額外下載素材。

## 測試入口

正常 App：首頁角色、招手／過來／坐下按鈕、跟小晴說話、設定 → 角色聲音與角色外觀。

Debug `AvatarProofActivity` 僅 shell 持有 DUMP 權限可開啟，用同一產品 renderer / audio provider 錄製受控動作，無永久 secret。

Room schema 3 → 4 為新增欄位 migration，沒有清空原角色、訊息、記憶、商城、相簿資料。Backup 可保留新的 body preset 與 optional full-body photo，旧備份補入預設值。

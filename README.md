# AI Life Companion 0.4.0

## Android 全身 3D 陪伴角色人工驗收版

# [⬇ 下載 APK](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.0-full-body/AI-Life-Companion-0.4.0.apk)

下載 → 安裝／更新 → 開啟。預設連接公開 HTTPS Backend，不需要 USB、電腦、ADB 或手動填 IP。

- Package：`com.ailifecompanion.app`
- versionName：`0.4.0`；versionCode：`6`
- 大小：120,075,464 bytes（120.08 MB / 114.51 MiB）
- SHA-256：`C622886BDB8860F4FB5988546BCAFFC4FBD93A3BE15AD547BE6E400059CBC6C9`
- 原始碼 commit：`b5210fcca4dcc5aefaa2ddb70cc7db05b5332bda`
- [Cloud Backend health](https://ai-life-companion-api.onrender.com/health)

## 這一版可以測什麼

原生 Filament / skinned glTF 全身角色。首頁試試「招招手」「過來一下」「坐下休息」；「跟小晴說話」使用 OpenAI Realtime，可插話。設定提供六種角色聲音與試聽。聊天、商城、旅行、相簿、Memory 與既有角色資料保留。

模型為風格化 3D 人物，不是寫實照片重建。照片用來建立本機臉部 reference、比例和膚色參數。舊版照片模式仍可選用。

## 6 支動態驗收影片

- [01 招手](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.0-full-body/01_wave.mp4)
- [02 走路／走近／走遠](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.0-full-body/02_walk.mp4)
- [03 坐下／站起](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.0-full-body/03_sit_stand.mp4)
- [04 表情](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.0-full-body/04_expression.mp4)
- [05 Realtime 語音與打斷](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.0-full-body/05_voice_chat.mp4)
- [06 嘴型同步](https://github.com/gavin1424/ai-life-companion-android-downloads/releases/download/v0.4.0-full-body/06_lipsync.mp4)

影片錄自 Pixel 7a profile / Android 36 模擬器，使用產品同一 renderer。語音為受控 PCM 輸入，連接真正 OpenAI 服務；音軌來自同次測試的輸入／播放 PCM 並按時間對齊。這不代表 Samsung 麥克風、喇叭、人聲自然度或 FPS 已實測。

## 驗證與已知限制

`test`、`lint`、`assembleDebug`、13 個 Backend tests、APK secret scan 已通過。公開後端已測聊天、記憶、TTS、三種 AI Action；Realtime 已完成兩輪音訊回覆與一次 truncate 打斷。

嘴型是音量與頻譜估計，不是精確 phoneme alignment。單一基礎 humanoid mesh；服裝目前以材質配色呈現。貓能走動、坐／趴、擺尾與玩耍，但尚無跳沙發動作。完整男性獨立 mesh、頭髮物理、服裝幾何替換、照片真人 3D 重建未完成。Render Free 冷啟動可能需要等待；保留測試費用限制。

[完整說明與素材授權](README_AVATAR_040.md) · [驗證資料](verification-0.4.0.json)

## 舊版本

[0.3.1 APK](https://raw.githubusercontent.com/gavin1424/ai-life-companion-android-downloads/main/AI-Life-Companion-0.3.1.apk)

# AI Life Companion 0.4.1 — 小晴、動作與聲音精修

保留既有 Filament / glTF 骨架引擎、聊天、Realtime、雲端 Backend、商城、旅行、相簿、Memory 與角色資料；可直接覆蓋安裝 0.4.0。

## 外觀：具體改動

- 以既有 `xiaoqing_selfie.webp`、`xiaoqing_side.webp` 為輪廓／髮型參考，調整臉寬、下顎、眼眶大小、眼距、鼻部深度、嘴寬。修改作用於 mesh 與每個 morph target，保留眨眼和嘴型。
- 深棕色肩長髮、髮尾弧度與層次，移除原髮材質的銅色自發光亮帶。
- 奶油色上衣、灰綠色寬褲、淺色鞋；不是完整的新衣服 mesh 系統。
- 修正貓和房間原始幾何的三角形朝向，恢復正常光照；增加窗簾、抱枕、畫框、書與咖啡杯，維持原家具碰撞配置。
- 首頁鏡頭拉近，既有互動改為圓角 tonal buttons。

### Character Likeness Pass

Reference → 既有 on-device ML Kit face box / contours / crop → 個人 headWidth / skin fitting → 小晴的 reference-guided 手動參數 fitting → 髮型、臉部／morph 一致變形 → 同一 Filament renderer 預覽。

`tools/character_likeness.py` 與 `assets/avatar/xiaoqing-likeness.json` 保留參數與參考來源。小晴的細部 fit 是對照照片的美術調整，不是自動照片到 3D 重建；尚不能把「照片本人辨識度」當成已取得人工認可。

## 動作：具體改動

- 依實際移動距離累積步伐相位，起步加速、接近目的地減速；手臂與對側腳同步。
- 支撐腳高度補償、抬腿膝彎與腳踝反向補償，減少腳底漂移。
- 招手分為抬臂、較小前臂擺動、手腕旋轉與放下；使用 smoothstep envelope。
- 坐／站採連續骨盆高度、前傾重心與向椅面移動，避免瞬間切 pose。
- 骨骼過渡與表情分開平滑；眨眼保留快速閉合，表情較慢過渡；聆聽時眉毛微抬。

## 語音與嘴型

沿用 OpenAI `gpt-4o-mini-tts` 與既有 Realtime。溫柔 preset 調至 0.96，自然 0.98，陪伴感 0.95；指令強調台灣中文、連貫語句、句意停頓、自然收尾，避免播報、逐字拖長或氣音表演。

設定 → 角色聲音：所有試聽統一為「嗨，今天過得怎麼樣？如果你累了，我可以陪你說說話。」新增陪伴感，保留其他聲音方案。公開 Backend 實際產出溫柔／自然／成熟三組 A/B/C 音檔；是否好聽由人工選擇，不以 HTTP 成功冒充自然度 PASS。

嘴型以相同播放 PCM 的 RMS、頻譜和過零率估計；最大開口降低至 0.72、降低幅度增益、兩幀 viseme 候選穩定後切換、相鄰 viseme 平滑，靜音回到 Rest。仍非精確 phoneme timing。

官方依據：[OpenAI Text to speech](https://developers.openai.com/api/docs/guides/text-to-speech)。

## 驗證範圍

Android `test`（12 個測試，各 Debug / Release）、`lint`、`assembleDebug`；Backend 13 tests。新增移動速度／停步與坐起連續性測試。使用既有 Pixel 7a / Android 36 模擬器，不代表 Samsung 麥克風、喇叭、FPS 或主觀品質已通過。

影片使用產品同一 renderer 的 debug 驅動。語音影片的音軌是同次雲端 TTS 返回並送往 AudioTrack 的 PCM，按播放時間對齊；Android screenrecord 本身不錄系統聲音，因此不是外部麥克風錄音。

## 素材與重建

既有 pixiv VRM Public License 1.0 繼續保留，詳見 `assets/avatar/avatar-license.json`。房間與貓為原始程式生成資產。無新增名人照片、秘密或外部帳號依賴。

```
python tools/build_avatar_assets.py
python tools/merge_vrm_avatar.py <licensed-reference.vrm>
gradlew.bat test lint assembleDebug
```

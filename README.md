# AI Life Companion 0.3.1

## Android 人工驗收測試版

### [⬇️ 下載 APK](https://raw.githubusercontent.com/gavin1424/ai-life-companion-android-downloads/main/AI-Life-Companion-0.3.1.apk)

下載 → 安裝 → 開啟。使用手機行動網路或 Wi-Fi 即可連接雲端 AI Chat、AI 合照及 TTS，不需要電腦、USB、ADB 或設定 IP。從 0.3.0 更新後會自動切換到 CLOUD。

> 免費雲端主機閒置後會休眠，首次連線可能需要 50 秒以上喚醒；請等待連線完成，若網路失敗可按「重新連線」。

| 項目 | 內容 |
| --- | --- |
| Package | `com.ailifecompanion.app` |
| versionName | `0.3.1` |
| versionCode | `5` |
| 檔案大小 | 79,069,581 bytes（79.07 MB） |
| SHA-256 | `02E1B692F2E49A9D943C2DDFFA837E58DF849E05C7A275AEB47172F9D7B48432` |
| 原始碼 commit | `4ed999f8d8af73f9c00ceac5a845827520ba17bb` |
| Backend | https://ai-life-companion-api.onrender.com |
| Health | https://ai-life-companion-api.onrender.com/health |

已完成公開 HTTPS API 回驗：OpenAI 串流聊天、記憶內容、GPT Image、TTS、匿名 session、無效 session 拒絕及限流。Android test、lint、assembleDebug 和 APK secret scan 已通過。這些結果不代表已完成本版 Samsung 手機 UI／麥克風／喇叭人工驗收。

OpenAI Key 只保存在雲端秘密環境設定，不包含在 APK 或此 Repository。AI 圖片每個安裝每日最多 3 次，冷卻 90 秒；測試購買不扣真錢。角色、聊天和相簿仍儲存在手機本機，建議保留備份。

[舊版 0.3.0（需要本機 Backend）](https://raw.githubusercontent.com/gavin1424/ai-life-companion-android-downloads/main/AI-Life-Companion-0.3.0.apk)

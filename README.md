# Lumière Wealth & Miles Dashboard

零伺服器、完全本機的銀行點數與航空里程戰略儀表板（v1.0 MVP）。

- 所有資料只存在使用者自己的瀏覽器（LocalStorage），不會傳到任何伺服器
- 不串接任何外部 API；PDF 解析用的 pdf.js 已經放在 `vendor/` 資料夾，不依賴 CDN
- 頁面設有 Content-Security-Policy，瀏覽器會擋下所有對外連線
- 加密備份：AES-GCM 256 + PBKDF2（310,000 次）

## 檔案結構

```
index.html               主程式（單一檔案）
favicon.svg              網站圖示
.nojekyll                讓 GitHub Pages 直接提供靜態檔案
vendor/pdf.min.js        pdf.js 3.11.174（Apache-2.0）
vendor/pdf.worker.min.js
vendor/pdfjs-LICENSE.txt
README.md
```

## 用 GitHub Pages 發布

1. 在 GitHub 建一個新的 repository，例如 `lumiere-dashboard`。
2. 點 **Add file → Upload files**，把這個資料夾裡的**所有檔案和 `vendor` 資料夾**一起拖進去，然後按 **Commit changes**。
   - 如果看不到 `.nojekyll`（Windows 預設隱藏以 `.` 開頭的檔案），少了它也能正常運作。
3. 到 **Settings → Pages**，Source 選 **Deploy from a branch**，Branch 選 `main`、資料夾選 `/ (root)`，按 **Save**。
4. 等一到兩分鐘，網址會是 `https://<你的帳號>.github.io/lumiere-dashboard/`。

## 使用須知

- 網站本身不存放任何人的資料。每位使用者、每台裝置、每個瀏覽器的資料都各自獨立。
- 老闆和秘書之間要同步資料，請用右上角的「備份」匯出加密檔，再透過安全管道傳給對方，對方用「還原」匯入。
- 清除瀏覽器資料或使用無痕模式都會讓資料消失，請定期備份。
- 內建的轉點比例、到帳時間、開賣天數都是示範資料，請在秘書模式的「規則設定」裡改成最新的官方公告。
- 免費版 GitHub 帳號只能對**公開 repository** 開啟 Pages，所以原始碼會公開（程式碼裡沒有任何個人資料）。頁面已加上 `noindex`，要求搜尋引擎不要收錄。

## 授權

- pdf.js © Mozilla，Apache License 2.0，見 `vendor/pdfjs-LICENSE.txt`。

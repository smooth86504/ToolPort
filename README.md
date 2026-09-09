# 個人工具箱 — GitHub Pages 部署步驟

檔案結構：
```
index.html                    ← 工具箱入口首頁
tools/aligner-schedule.html   ← 牙套週期計算器
```

## 1. 建立 repository

1. 到 https://github.com/new 建立一個新 repo，例如叫 `my-tools`
2. Visibility 選 **Private**（見下方「隱私權注意事項」）
3. 建立完成後，把這個資料夾裡的 `index.html` 和 `tools/` 整個上傳：
   - 網頁介面：開啟 repo 頁面 → **Add file → Upload files** → 把 `index.html` 和 `tools` 資料夾拖進去 → Commit
   - 或用命令列：
     ```bash
     cd 這個資料夾的路徑
     git init
     git add .
     git commit -m "first deploy"
     git branch -M main
     git remote add origin https://github.com/你的帳號/my-tools.git
     git push -u origin main
     ```

## 2. 開啟 GitHub Pages

1. 進入 repo 的 **Settings → Pages**
2. Source 選 **Deploy from a branch**
3. Branch 選 **main**，資料夾選 **/(root)**，按 Save
4. 等 1～2 分鐘，畫面會顯示網址，格式類似：
   `https://你的帳號.github.io/my-tools/`

之後要新增工具，把新的 HTML 放進 `tools/` 資料夾，並在 `index.html` 的 `.grid` 裡多加一個 `<a class="app">` 圖示、指到新檔案的相對路徑，再 push 一次即可。

## 隱私權注意事項（重要）

GitHub Pages 目前的規則是：

- **免費方案（Free）**：即使原始 repo 設為 Private，只要開啟 GitHub Pages，產生出來的網站本身**還是任何人拿到網址就能看**，不會要求登入 GitHub。也就是「知道連結的人可以看」，跟你原本 Claude Artifact 的私密程度差不多，但沒有密碼保護。
- **GitHub Pro / Team / Enterprise Cloud**：可以在 Settings → Pages 額外開啟「Private」可視性，這樣網站只有你（或被邀請進 repo 的人）登入 GitHub 帳號後才能看，其他人連結打開會被要求登入且無權限。

如果你只用免費帳號、又想要比「連結持有者可看」更強的保護，可以考慮：
- 用 Netlify／Vercel 部署後，另外開啟密碼保護（部分方案免費即有）
- 或維持用 Claude Artifact，也是連結制、不會被公開搜尋到

Sources:
- https://github.blog/changelog/2021-01-21-access-control-for-github-pages/
- https://docs.github.com/en/enterprise-cloud@latest/pages/getting-started-with-github-pages/changing-the-visibility-of-your-github-pages-site

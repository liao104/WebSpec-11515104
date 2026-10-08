# 第2次作業(3%)
- 學號：(請務必填寫)
- 姓名：(請務必填寫)
- 信箱：(請務必填寫)

![](../images/week2-1.png)

## 作業目標

### 一、VSCode + Extensions + Git 使用一鍵安裝：
1. 請於以下連結下載後，並**以系統管理員身分執行**：[下載](https://ocu.tw/download/VSCodeAI.exe)
- 請參考以下載圖執行：點擊檔案後按右鍵，選擇以系統管理員身分執行
   ![](../images/以系統管理員身分執行.png)
- 此一鍵安裝檔，包括以下內容
   1. VSCode：Visual Studio Code 
   ![](../images/Visual_Studio_Code.png)
   2. VSCode Extensions
      1. 中文化：Chinese (Traditional) Language Pack for Visual Studio Code
      2. Markdown工具：
         1. Markdown Preview Enhanced
         2. Markdown All in One
      3. AI工具：
         1. Google Antigravity
         2. Codex - OpenAI's coding agent
      4. 網頁瀏覽工具：Live Server
   3. Git for Windows

### 二、VSCode Git Clone：
1. 選擇放置儲存庫的資料夾：`D:\Web`
2. 開啟終端機，輸入git指令
- 請將EMail信箱更換為GitHub的申請信箱
```shell
git config --global user.email EMail信箱
```
- 請將GitHub帳號更換為GitHub帳號
```shell
git config --global user.name GitHub帳號
```
3. 由GitHub複製Repo：WebSpec_學號
- GitHub網址：https://github.com/(GitHub名稱)/WebSpec_學號
```shell
git clone [貼上WebSpec網址]
```
4. 由GitHub複製Repo：WebPage_學號
- GitHub網址：https://github.com/(GitHub名稱)/WebPage_學號
```shell
git clone [貼上WebPage網址]
```

### 三、在VSCode上修改 work2.md
1. 選擇資料夾(WebSpec_學號)中的/works/work2.md檔案：
2. 修改以下欄位
   1. 學號：(開頭不含s)
   2. 姓名：(請填寫真實姓名)
   3. 信箱：(GitHub申請的信箱)
3. 儲存檔案
4. 在VSCode上提交及推送
   1. 版本說明：⚠️(必填)
   2. 提交與推送
      ![](../images/VSCodeCommitPush.jpg)

### 四、VSCode修改 outline.md
1. 選擇資料夾(WebSpec_學號)中的/specs/outline.md檔案：
2. 修改以下欄位(請務必修改內容)
   1. 網站名稱：(如自創品牌咖啡店)
   2. 用途：(如推廣手沖咖啡)
   3. 目標受眾：(如手沖咖啡喜好者)
   4. 品牌風格：(如高階咖啡豆)
   5. 品牌顏色：(如藍色)
   6. 功能：(如吸引客戶消費咖啡)
3. 儲存檔案
4. 在VSCode上提交及推送
   1. 版本說明：⚠️(必填)
   2. 提交與推送

## 評分方式

### 檢查項目：完成後請打勾
- [ ] 在VSCode上修改/WebSpec/works/work2.md：學號、姓名
- [ ] 在VSCode上儲存、填寫訊息、提交及推送：在GitHub上確認已同步內容
- [ ] 在VSCode上修改/WebSpec/specs/簡要大綱.md：填寫每一項內容
- [ ] 在VSCode上儲存、填寫訊息、提交及推送：在GitHub上確認已同步內容

> [!important]
> 請於上課時完成，若未到課同學，請於下次上課(**第3週**)前完成

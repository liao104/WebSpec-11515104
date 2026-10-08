# 第3次作業(3%)
- 學號：(請務必填寫)
- 姓名：(請務必填寫)
- 信箱：(請務必填寫)

![](../images/week3-1.png)

## 作業目標

### 一、VSCode + Extensions + Git 使用一鍵安裝：
1. 請於以下連結下載後，並**以系統管理員身分執行**：[下載](https://ocu.tw/download/VSCodeAI.exe)

### 二、VSCode複製GitHub上2個儲存庫Repo
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

### 三、註冊AI工具：
1. Google Antigravity：
   1. Sign in：Continue with Google
![](../images/AntigravitySignin.png)
2. Codex：
   1. 安裝VSCode Codex Extension
      1. VSCode打開延伸模組：**Codex – OpenAI’s coding agent**
      2. 使用ChatGPT登入：使用Codex需手機驗證
   2. 安裝ChatGPT單機版[連結](https://chatgpt.com/)
      1. 切換為Codex模式，需使用手機驗證

### 四、在VSCode上修改/WebSpec_學號/works/work3.md
1. 修改學號及姓名，並儲存檔案
2. 填寫版本說明，並提交及推送

### 五、使用AI工具製作網頁
1. 開啟AI工具視窗或單機版程式(以下以Codex為例)
2. VSCode + Codex Extension製作網頁
   1. 使用VSCode開啟/WebSpec_學號/specs/**outline**.md
   2. 開啟Codex側邊對話框，輸入以下提示詞
      ```htm
      請依據目前開啟的內容為網頁規格，製作一個網頁index.html，並儲存於資料夾：WebPage_學號/outline/中
      ```
   3. 終端機出現詢問是否允許操作指令
      1. 請回答允許一次/允許類似指令
      2. 請將變更權限方式改為：代為核准
3. 檢查/WebPage/**outline**/index.html網頁內容
4. 以瀏覽器或Live Server Extension檢視網頁

### 六、在VSCode將資料夾/WebPage/outline上傳至GitHub
1. 請於GitHub平台上確認資料已上傳成功

### 七、使用AI工具逆向製作網頁規格
1. 使用VSCode開啟/WebPage_學號/outline/index.html
2. 開啟Codex側邊對話框，輸入以下提示詞
   ```htm
   請依據目前開啟的網頁檔案，讀取內容逆向製作一個完整網頁規格Markdown文件，並儲存以下檔案：WebSpec_學號/specs/detail.md中，以便更精確修改規格來製作網頁
   ```
3. 檢查/WebSpec_學號/specs/detail.md網頁規格
4. 以VSCode側邊預覽Markdown網頁規格

## 評分方式
- 檢查項目：完成後請打勾
    - [ ] 在VSCode上修改/WebSpec_學號/works/work3.md：填寫學號、姓名，並同步於在GitHub上
    - [ ] 在VSCode使用AI工具以outline.md生成/WebPage_學號/outline/index.html網頁，並同步於在GitHub上
    - [ ] 在VSCode使用AI工具以index.html逆向生成/WebSpec_學號/specs/detail.md網頁規格，並同步於在GitHub上
    - [ ] 在GitHub上確認以上檔案是否完全同步內容

> [!important]
> 請於上課時完成，若未到課同學，請於下次上課(**第4週**)前完成

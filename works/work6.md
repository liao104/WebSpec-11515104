# 第6次作業(3%)
- 學號：(請務必填寫)
- 姓名：(請務必填寫)

## 作業目標
1. VSCode複製GitHub上2個儲存庫Repo
   1. 在電腦建立資料夾：D:\Web
      1. 目的為存放以下2個Repo
   2. 由GitHub複製Repo：WebSpec_學號
      1. GitHub網址：https://github.com/(GitHub名稱)/WebSpec_學號
      2. 存放資料夾：D:\Web
   3. 由GitHub複製Repo：WebPage_學號
      1. GitHub網址：https://github.com/(GitHub名稱)/WebPage_學號
      2. 存放資料夾：D:\Web
2. 在VSCode上開啟/WebSpec_學號/specs/onepage1.md
   1. 另存為/WebSpec_學號/specs/onepage2.md
3. 修改/WebSpec_學號/specs/onepage2.md
   1. 修改5.5 沖煮日常區域，目標為增加一個崁入式的YouTube影片
      1. 進入YouTube網站中，找到影片的編號
         1. 請找到影片的網址如下：
         ```html
         https://www.youtube.com/watch?v=hMOYa4EBntI
         ```
         2. 請於網址中找到影片的編號
      2. 將版面的內容改為：
      ```htm
      左為影片崁入
      ```
      3. 在hero區域，增加以下內容
      ```html
      **影片崁入**

      - 使用 `<iframe>` 元素顯示
      - Youtube編號：hMOYa4EBntI
      - 寬度：560px
      - 高度：315px
      ```
4. 在VSCode將檔案/WebSpec_學號/specs/onepage2.md上傳至GitHub
5. 使用AI工具製作網頁
   1. 開啟AI工具視窗或單機版程式(以下以Codex為例)
   2. VSCode + Codex Extension製作網頁
      1. 使用VSCode開啟/WebSpec_學號/specs/**onepage2**.md
      2. 開啟Codex側邊對話框，輸入以下提示詞
         ```htm
         請依據目前開啟的內容為網頁規格，製作一個網頁index.html，並儲存於資料夾：WebPage_學號/**onepage2**/中
         ```
   3. 檢查/WebPage_學號/**onepage2**/index.html網頁內容
   4. 以瀏覽器或Live Server Extension檢視網頁
6. 在VSCode將資料夾/WebPage_學號/onepage2上傳至GitHub
   
## 評分方式
- 檢查項目：完成後請打勾
    - [ ] 在VSCode上修改/WebSpec_學號/works/work6.md：填寫學號、姓名，並同步於在GitHub上
    - [ ] 在VSCode上複製/WebSpec_學號/specs/onepage2.md：修改各項內容後，並同步於在GitHub上
    - [ ] 在VSCode使用AI工具以onepage2.md生成/WebPage_學號/onepage2/index.html網頁，並同步於在GitHub上
    - [ ] 在GitHub上確認以上檔案是否完全同步內容
> [!important]
> 請於上課時完成，若未到課同學，請於下次上課(**第7週**)前完成

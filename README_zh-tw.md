# Learn-by-one-question

<h2>Security</h2>

<details id='defenseInDepth'>
  <summary><b>深度防禦</b>: 什麼是深度防禦，深度防禦有哪些層，其分別的定義為何？</summary>
<br>
<b>Answer:</b>  

- Physical: 在真實世界保護設備之安全
- Identity & access: 確保資料存取符合認證與授權並以RBAC為標準
- Perimeter: 防禦DDOS、防火牆
- Network: 只允許必要的IP範圍提供存取、子網路切割
- Compute: 確保作業系統保持更新、沒有惡意程式碼
- Application: 確保程式沒有安全性弱點，沒有存放敏感資料
- Data: 確保資料存取受到保護
</details>

<details>
  <summary><b>零信任</b>: 零信任的架構與傳統架構有何差異？</summary>
<br>
<b>Answer:</b> 

傳統架構只把防火牆與身分認證設置於網路邊界，進入內網後即信任該使用者的身分。
而零信任架構以切割多層網路，隨時假定前一層可能已經被滲透。在不同層與不同服務之間，仍然設置防火牆、白名單、帳號安全認證、最小授權原則，並時時監控危險徵兆，於邊界網路也通常會設置MFA。
</details>

### Identity and access management

<details id='MFA'>
  <summary><b>MFA</b>: MFA對用戶體驗有什麼影響？如何平衡安全性和用戶體驗？</summary>
<br>
<b>Answer:</b>  

由於需要通過多種驗證方式才能夠通過驗證，因此使用者的體驗會較差。為了平衡安全性，可以採用簡化使用者操作的驗證方式，例如Passwordless的方式，Passwordless可採用手機裝置偕同驗證，或是指紋的方式來確認使用者的身分。或是採用Conditional access的方式，智能的判斷使用者當下的位置、動作若有較高疑慮，則需要通過更多的驗證。
</details>

<details id='RBAC'>
  <summary><b>RBAC</b>: RBAC相關的重要設計原則</summary>
<br>
<b>Answer:</b>  

- 以角色為基礎的存取原則 (Role based access control)：取代傳統以動作為基礎的權限控管架構，以抽象化的各系統角色為基礎，進行權限控管。設定該角色可執行的動作清單，再分配人員至角色。減少權限控管的複雜度並降低錯誤的可能性。
- 最小權限原則 (Least privilege)：應該給予該角色所需的最小權限，以減少過度提供權限的安全性風險。
- 分離職責原則 (Separation of duties)：減少不同角色間的權限重疊度，減少特定角色被滲透或內部成員濫用權力的風險。
- 分層權限原則：針對資源的重要性與敏感度，設定不同的權限控管層級。謹慎控管高層級權限的授權範圍，以減少高風險資源的被濫用或洩漏的風險。
</details>



<details id='OAuth2'>
  <summary><b>OAuth2</b>: 簡介Oauth2重要角色與授權流程</summary>
<br>
<b>Answer:</b>  

角色包含：客戶端、資源提供者、授權提供者
授權流程：

1. 客戶端向資源提供者請求資源
2. 資源提供者判斷客戶端無權限資料，請客戶端重新導向到授權提供者。
3. 客戶端向授權提供者完成身分認證，授權提供者發給以其私鑰簽署的Access Token
4. 客戶端拿著Access Token向資源提供者請求資源
5. 資源提供者使用公鑰判斷Access Token有效，並且效期與內容無誤。允許存取資源。
</details>


<details id='JWT'>
  <summary><b>JWT</b>: JWT的核心觀念是甚麼？JWT的優點為何？</summary>
<br>
<b>Answer:</b>  

- JWT的核心觀念將授權資訊與簽章內容以一個開放的標準共同存放，讓這個授權資訊易於交換。
- 優點：
  - 無狀態：JWT本身即包含授權資訊與簽章內容，伺服器不需要存放額外資訊，提高伺服器容錯與伸縮性
  - 安全性高：JWT包含簽章資訊，防止資料被竄改
  - 跨域使用：將JWT放入HTTP Header的Authorization之中，即可跨domain進行身分認證
  - 跨平台使用：JSON標準格式，各環境都易於產生與驗證
  - 可擴展：JWT可放置自定義屬性，提供更多授權資訊
</details>

### Network Security

<details id='sub-network'>
  <summary><b>子網路切割</b>: 如何切割大型企業網路，各部門需要自己的獨立子網路，並允許跨部門通訊?</summary>
<br>
<b>Answer:</b>  

- 分割：按照每個部門預計大小切割網域
- 連結：統計部門間連線需求，並預估流量大小，設定足夠的路由器
- 備援：當監測到停止服務時，自動切到備援的網路與路由器
- 資安
  - 在網域之間設置防火牆，並開放允許通訊的IP白名單，留存網路傳輸紀錄
  - IDS (入侵偵測系統)：監控網路流量，偵測入侵威脅
  - IPS (入侵防禦系統)：監控網路設備，偵測可疑流量與執行的可疑指令
</details>


<details id='firewall'>
  <summary><b>防火牆</b>: 簡介防火牆常見的防護機制</summary>
<br>
<b>Answer:</b>  

- 第4層防火牆
  - 允許特定IP
  - 允許特定Port
- 第7層防火牆
  - 允許特定網址
  - 允許特定header
  - Web application firewall
    - 檢查是否有XSS, SQL injectction等攻擊字串
  - 狀態機防火牆
    - 紀錄此IP前後行為，判斷是否有風險
</details>



<details id='vpn'>
  <summary><b>VPN</b>: 雲端架構中使用VPN的優點和缺點是甚麼？</summary>
<br>
<b>Answer:</b>  

優點：

- 可以在公共網路之上建立安全的加密連線。
- 建立多個不同區域的私有網路間的通訊
- 讓遠端工作者可以安全的連接私有網路
- 可提供網路應用程式額外的一層安全防護

缺點：

- 由於加解密需要計算資源，所以會減慢傳輸速度。
- 技術較複雜且需要額外連接設備，因此管理與架設成本更高
- VPN設施有被DDOS等網路攻擊的風險
</details>

### Web應用安全

<details id='xss'>
  <summary><b>XSS</b>: 簡介XSS中的反射型、儲存型、DOM型，XSS風險的預防方式為何？</summary>
<br>
<b>Answer:</b>  

- 反射型：超連結網址、cookie或表單中包含XSS字串，若後端使用這些資料動態組成前端網頁，則顯示網頁時XSS程式被執行。
- 儲存型：若DB資料包含XSS字串，由DB資料動態組成前端網頁時，網頁執行XSS程式。
- DOM型：若Ajxx回傳XSS字串。當使用此字串直接放入網站DOM時，網頁執行XSS程式。

預防XSS的方式為
- 以CSP（Content Security Policy）限制網頁執行具有風險性的內容
- 對輸出資料進行HTML encoding，避免顯示具有風險性的內容
- 檢查傳到後端的資料，避免使用、儲存具有風險性的內容
</details>

<details id='CSRF'>
  <summary><b>CSRF</b>: 請給我一個CSRF攻擊的範例情境，並說明如何防範這個攻擊。</summary>
<br>
<b>Answer:</b>  

攻擊的範例情境如下：
背景: 使用者在已經登入攻擊目標網站的情況下，瀏覽器存有此網站的cookie。
攻擊: 使用者造訪高風險網站，此網站有一個圖片或超連結將會發送帶有攻擊內容的Request給攻擊網站。
此時由於Request中帶有原本的登入時獲得的cookie，因此目標網站信任此request，因此遭受攻擊。
防範此攻擊的方式是

1. Server端檢查request header中的origin是不是同一domain，若不通過則捨棄此request
2. Server端產生網頁時，固定都會生成一個CSRF token，此token存放於session而非cookie。每次請求時，都需要攜帶此token以判斷是否來自正確的網頁。
</details>

<details id='sql-injection'>
  <summary><b>SQL Injection</b>: 如何防止 SQL injection 攻擊？</summary>
<br>
<b>Answer:</b>  

SQL injection 攻擊是指直接把不可信任的變數直接串上 SQL 字串，若此變數內含攻擊內容，則資料庫可能會被攻擊或取出未經授權的資料。避免 SQL injection 的方法有兩種：

1. 不要直接把不可信任的變數串上 SQL 字串，而是使用元件傳遞變數的方式。例如，在 Java 中可以使用 PreparedStatement 來傳遞變數：
    
    有SQL injection 風險的範例
    
    ```java
    String title = request.getParameter("title"); // 從前端傳來的變數
    String sql = "SELECT * FROM booking WHERE title = " + title;
    Statement stmt = conn.createStatement();
    stmt.executeQuery(sql);
    ```
    
    修正後的範例
    
    ```java
    String title = request.getParameter("title"); // 從前端傳來的變數
    String sql = "SELECT * FROM booking WHERE title = ?";
    PreparedStatement stmt = conn.prepareStatement(sql);
    stmt.setString(1, title);
    stmt.executeQuery();
    ```
    
2. 檢查不可信任的變數是否包含危險字串或非預期的內容，例如單引號、分號等。如果包含危險字串，則拋出錯誤或進行適當的處理。
</details>


<details id='csp'>
  <summary><b>Content Security Policy</b>: Content Security Policy主要設定那些內容，並可以防範那些攻擊？</summary>
<br>
<b>Answer:</b>  

Content Security Policy(CSP)可以分別設定各種資源允許載入的來源，以及是否允許inline js和css，也可以設定是否僅允許HTTPS請求。藉由CSP可以防範XSS, 跨站請求偽造等攻擊。
</details>


<details id='same-origin-policy'>
  <summary><b>同源政策</b>: 簡介Same-origin policy，如果需要允許來自不同源頭的網頁相互訪問，該如何實現？</summary>
<br>
<b>Answer:</b>  

Same-origin policy是一種瀏覽器安全機制，此機制不允許其他網域的js存取目前網站的cookie, dom, localStorage, indexedDB，呼叫其他網域的ajax也會受到限制。以減少XSS, cookie洩漏等外部攻擊的風險。
如果想要存取其他網域的資源，可以通過跨域資源共享(CORS)實現。CORS藉由response header增加Access-Control-Allow-Origin來允許其他網域的資源。
</details>


### 資料安全

<details id='symmetric-encryption'>
  <summary><b>對稱式加密</b>: 說明對稱式加密的優缺點及解決缺點的方式</summary>
<br>
<b>Answer:</b>  

優點：加解密的速度較快，適合傳輸資料使用。
缺點：由於加密與解密都是使用同一個金鑰，因此若使用網路傳輸金鑰，會有安全性的問題。
可使用金鑰交換技術以安全的產生可溝通的金鑰，例如：

- 使用RSA加密傳輸金鑰
- Deffie-Hellman算法產生互相溝通的金鑰
</details>


<details id='asymmetric-encryption'>
  <summary><b>非對稱式加密</b>: 在使用非對稱式加密時，何時需要使用公鑰，何時需要使用私鑰？請說明其中的差異與原因。</summary>
<br>
<b>Answer:</b>  

非對稱式加密中，先產生一組公私鑰。私鑰並不會在網際網路上傳輸，而只會傳輸公鑰。對方取得公鑰後，私鑰擁有者以私鑰對訊行進行加密或簽章，對方若可以用對應公鑰成功解開，代表此訊息的確來自私鑰擁有者，並且訊息未經變照。
總結來說，私鑰保持原地，並用於加密、簽章。公鑰傳輸對方，用來解密、驗證簽章。
</details>

<details id='hash-algorithm'>
  <summary><b>Hash算法</b>: Hash演算法的簡介及用途</summary>
<br>
<b>Answer:</b>  

簡介:
- 其目的為經由壓縮與轉換，以產生摘要。
- 其特性為同樣原文會產生固定的Hash值，且無法經由Hash值反推原文的內容。
- 有多種Hash演算法的實現，例如MD5, SHA
- 有些Hash算法已經被認為是不安全、應避免使用的。例如MD5, SHA1。應審慎選擇Hash算法
- 可使用Salt以增加Hash算法的破解難度。

用途:
- 數字簽名: 將內文產生hash值，並以私鑰進行加密合併內文傳送，用以驗證內文未被變造。
- 密碼儲存: 將密碼轉為hash值存入資料庫。使用者登入時，將輸入的密碼轉換為Hash值進行比對驗證。即使駭客取得資料庫權限，由於資料庫中記錄的是無法還原的Hash值，因此可避免密碼外洩。
</details>


<details id='digital-signature'>
  <summary><b>數位簽名</b>: 簡介數字簽名流程</summary>
<br>
<b>Answer:</b>  

1. 產生端將原始文件內容以Hash算法產生數字摘要
2. 產生端使用私鑰進行加密產生數字簽名
3. 驗證端以公鑰進行解密數字簽名，還原得到數字摘要
4. 驗證端將收到的文件內容以同樣Hash算法產生數字摘要
5. 驗證端比對數字摘要是否一致，以判斷文件是完整的原始文件，且此文件是由信任的單位產生
</details>






<h2 id="object-oriented">Object-Oriented</h2>

### SOLID Principles

<details id='SRP'>
  <summary><b>單一職則原則</b>: 解釋並舉例說明單一職則原則</summary>
<br>
<b>Answer:</b>  

一段程式，例如：類別、介面或函數應該只負責單一職責，以減少程式耦合度、提高可讀性、可維護性、可測試性。
例如，假設有一個書籍訂單系統，訂單管理、訂單正確性檢查、訂單SQL應分為不同的類別。
</details>


<details id='ISP'>
  <summary><b>介面隔離原則</b>: 解釋並舉例說明介面隔離原則</summary>
<br>
<b>Answer:</b>  

為了提高程式碼的可讀性與可維護性，類別不應該強制實作其不需要的方法。因此，若在某些情況下，某個介面的某些功能不需要被實作，這個介面應該被拆分為多個介面。舉例來說，如果原本有一個負責查詢與修改資料的介面叫做DataManager，但有些情況只需要實作查詢介面，那麼DataManager 應該被拆分為DataReader 與DataModifier 兩個介面。
</details>

<details id='LSP'>
  <summary><b>里氏替換原則</b>: 如果子類別沒有按照里氏替換原則設計，可以能發生甚麼問題? 如果子類別需要與父類別不一樣的功能，應該要怎麼處理？</summary>
<br>
<b>Answer:</b>  

如果子類別沒有按照里氏替換原則。由於其他程式並不 一定知道此父類別程式的具體實作類別，當子類別的行為與父類別有衝突時，呼叫的程式可能會產生錯誤。子類別應該保持與父類別的行為一致，只是針對細節做出更多補充。如果真的需要不同的功能，代表應該分出不同的類別，而不在此父類別的繼承。
</details>

<details id='OCP'>
  <summary><b>開放封閉原則</b>: 請問有哪些方式可以達到開放封閉原則?</summary>
<br>
<b>Answer:</b>  

開放封閉原則是指應該對擴展功能開放，並對現有程式修改封閉。為達到此原則，可以使用繼承、多型或設計模式等方式實現
具體來說，包含下列幾種常見方式

1. 繼承: 子類別可以在繼承父類別現有功能的情況下，針對差異的部分進行覆寫。實作介面也可以達到類似的作法。
2. 多型: 同樣的一個方法，在不同傳入值的情況下，可有不同的實作。因此增加不同的傳入值，以處理不同的情況，以避免改變現有方法。
3. 設計模式中有許多針對彈性設計的經典解法，像是可以使用Builder模式以提供彈性建立物件的方式；Decortor模式可以動態添加額外功能；依賴注入模式將變動的邏輯抽成獨立的介面，依照傳入的介面實作不同，而有不同的處理邏輯。
</details>


<details id='DIP'>
  <summary><b>依賴反轉原則</b>: 如何實現依賴反轉原則？</summary>
<br>
<b>Answer:</b>  

依賴反轉原則是指高階模組使用元件時，元件只需指定回傳的介面，而非具體的類別。以減少程式偶合度。
具體實現實現依賴反轉原則的方式可通過

1. 依賴注入：元件指定回傳的介面，使用時元件動態決定類別的實現方式，而非由高階模組決定類別的實現方式。或元件提供setter方法。
2. 依賴尋找：使用例如Spring的容器管理機制，由容器動態回傳該類別的實作物件。
</details>


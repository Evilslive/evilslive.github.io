
### Web Server Gateway Interface,  WSGI

#### Gunicorn 

``` cmd
gunicorn wsgi:app
gunicorn --workers=4 wsgi:app
gunicorn --bind=10.1.0.0:8080 wsgi:app
```

#### Werkzeug

```
```

### HTTP 請求方式

#### GET >     請求展示指定資源。只應用於取得資料。
#### HEAD >    請求與 GET 方法相同的回應，但它沒有回應主體(response body)。
#### POST >    用於提交指定資源的實體，通常會改變伺服器的狀態或副作用(side effect)。
#### PUT >     取代指定資源所酬載請求（request payload）的所有表現。
#### DELETE >  刪除指定資源.
#### CONNECT > 和指定資源標明的伺服器之間，建立隧道（tunnel）。
#### OPTIONS > 描述指定資源的溝通方法（communication option）。
#### TRACE >   與指定資源標明的伺服器之間，執行迴路返回測試（loop-back test）。
#### PATCH >   用指定資源的部份修改。


### HTTP 狀態碼

#### 資訊回應

> 100 Continue
此臨時回應表明，目前為止的一切完好，而用戶端應當繼續完成請求、或是在已完成請求的情況下，忽略此資訊。

> 101 Switching Protocol
此狀態碼乃為用戶端 Upgrade (en-US) 請求標頭發送之回應、且表明伺服器亦切換中。

> 102 Processing (WebDAV (en-US))
此狀態碼表明伺服器收到並處理請求中，但目前未有回應。

> 103 Early Hints (en-US)
此狀態碼主要與 Link (en-US) 標頭有關：它能讓用戶代理（user agent）能在伺服器準備回應前能 preloading (en-US) 資源。

#### 成功回應

> 200 OK
請求成功。

> 201 Created
請求成功且新的資源成功被創建，通常用於 POST 或一些 PUT 請求後的回應。

> 202 Accepted
此請求已經被接受但尚未處理。此狀態為非承諾性，代表 HTTP 無法在之後傳送一個非同步的回應告知請求的處理結果。最初目的為外部程序或其他伺服器處理請求的情況，或用於批次處理中。

> 203 Non-Authoritative Information
此回應碼表示回傳的中介資料集與並非與原始伺服器上的有效確定集合完全相同，而是來自本地或第三方的副本。除此情況外，200 OK 回應碼應該被優先使用。

> 204 No Content
傳送的請求沒有內容, 但headers內有資訊.

> 205 Reset Content
請求刷新頁面

> 206 Partial Content
分流下載?

> 207 Multi-Status (WebDAV (en-US))
多狀態響應?

> 208 Multi-Status (WebDAV (en-US))
用以避免多狀態響應時, 反覆請求?

> 226 IM Used (HTTP Delta encoding)
已完成GET請求?

#### 重定向訊息

> 300 Multiple Choice
請求擁有一個以上的回應。用戶代理或使用者應該從中選一。不過，並沒有標準的選擇方案。

> 301 Moved Permanently
此回應碼的意思是，請求資源的 URI 已被改變。有時候，會在回應內給予新的 URI。

> 302 Found (en-US)
請求的URI已暫時改變了, 正在等待完成?

> 303 See Other (en-US)
伺服器傳送請求到其他位址, 以取得URI與GET資源

> 304 Not Modified (en-US)
暫存未被修改, 告知可繼續使用.

> 305 Use Proxy 
在舊版本的 HTTP 規範中，表示請求資源必須透過代理存取。基於對代理的頻內設置 (in-band configuration) 相關的安全考量，該狀態碼已棄用。

> 306 unused
該狀態碼已不再被使用，僅被保留。該狀態碼曾在先前得的 HTTP 1.1 規範中被使用。

> 307 Temporary Redirect (en-US)
伺服器發送此回應來使客戶端保持請求方法不變向新的地址發出請求。 與 302 Found 相同，差別在於客戶端不許變更請求方法。例如，應使用另一個 POST 請求來重複發送 POST 請求。

> 308 Permanent Redirect (en-US)
URI以永久更改, 請求方法將延續使用?

#### 用戶端錯誤回應

> 400 Bad Request (en-US)
此回應意味伺服器因為收到無效語法，而無法理解請求。

> 401 Unauthorized (en-US)
需要授權以回應請求。它有點像 403，但這裡的授權，是有可能辦到的。

> 402 Payment Required (en-US) 
此回應碼留作未來使用。一開始此碼旨在用於數位交易系統，然而，目前極少被使用，且不存在標準或慣例。

> 403 Forbidden
用戶端並無訪問權限，例如未被授權，所以伺服器拒絕給予應有的回應。不同於 401，伺服端知道用戶端的身份。

> 404 Not Found
伺服器找不到請求的資源。因為在網路上它很常出現，這回應碼也許最為人所悉。

> 405 Method Not Allowed (en-US)
伺服器理解此請求方法，但它被禁用或不可用。有兩個強制性方法：GET 與 HEAD，永遠不該被禁止、也不該回傳此錯誤碼。

> 406 Not Acceptable (en-US)
伺服器根據請求找不到資源?

> 407 Proxy Authentication Required (en-US)
類似401, 但須透過Proxy完成身分驗證

> 408 Request Timeout (en-US)
伺服器回應超過設定時間?

> 409 Conflict
表示請求與伺服器目前狀態衝突

> 410 Gone (en-US)
請求的資源已經不在.

> 411 Length Required
伺服器拒絕該請求，因為 Content-Length 頭沒有被定義，然而伺服器要求。

> 412 Precondition Failed (en-US)
用戶端的header不符合要求

> 413 Payload Too Large (en-US)
請求的實體資料大小超過了伺服器定義的上限，伺服器會關閉連接或返回一個 Retry-After 回應頭。

> 414 URI Too Long (en-US)
客戶端的 URI 請求超過伺服器願意解析的長度。

> 415 Unsupported Media Type
被請求資源的多媒體類型不被伺服器支援，因此該請求被拒絕。

> 416 Requested Range Not Satisfiable (en-US)
數據太大?

> 417 Expectation Failed (en-US)
伺服器無此請求方式?

> 418 I'm a teapot
伺服器拒絕用茶壺泡咖啡... XDD

> 421 Misdirected Request
新的定向失敗

> 422 Unprocessable Entity (en-US) (WebDAV (en-US))
請求格式正確, 但"語意"錯誤?

> 423 Locked (WebDAV (en-US))
被訪問的資源被鎖定。

> 424 Failed Dependency (WebDAV (en-US))
由於先前的請求失敗導致此請求失敗。

> 426 Upgrade Required (en-US)
請用戶端升級

> 428 Precondition Required (en-US)
有條件的接受請求, 避免遺失更新, 如用戶端GET資源並修改後, PUT回來時.

> 429 Too Many Requests (en-US)
用戶在給定的時間內 ("rate limiting") 發送了過多的請求。

> 431 Request Header Fields Too Large (en-US)
伺服器不願意處理該請求，因為標頭欄位過大。該請求可能可以在減少請求標頭欄位大小後重新提交。

> 451 Unavailable For Legal Reasons
用戶端請求違法的資源，例如受政府審查的網頁。

#### 伺服器端錯誤回應

> 500 Internal Server Error
伺服器端發生未知或無法處理的錯誤。

> 501 Not Implemented (en-US)
請求方法不支持 (GET, HEAD)?

> 502 Bad Gateway
伺服器關閉或離線?

> 503 Service Unavailable
伺服器開著, 但停止運作或過載?

> 504 Gateway Timeout
伺服器無法及時回應

> 505 HTTP Version Not Supported (en-US)
請求使用的 HTTP 版本不被伺服器支援。

> 506 Variant Also Negotiates (en-US)
伺服器內部配置錯誤: 循環引用?

> 507 Insufficient Storage (en-US)
伺服器內部配置錯誤: 存取變動的資源?

> 508 Loop Detected (en-US) (WebDAV (en-US))
無限循環/死結

> 510 Not Extended (en-US)
請求是未來更新才能處裡的

> 511 Network Authentication Required (en-US)
用戶端需獲得權限才能訪問

[以上由MDN頁面修改](https://developer.mozilla.org/zh-TW/)
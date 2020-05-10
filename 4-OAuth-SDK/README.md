# 章節四 Forge OAuth、Forge 服務整體及 SDK 簡介

## Forge OAuth

### OAuth 是什麼

OAuth 是一種開放授權標準、是一種 [OpenID](https://zh.wikipedia.org/wiki/OpenID) 的擴充，允許用戶讓第三方應用透過權杖(Access Token) 在特定時間內（如一個小時內）存取該用戶在某一網站上儲存受保護的資源（如相片，影片，聯絡人列表），而無需將用戶名稱和密碼提供給第三方應用的一種授權機制 ([Ref: Wikipedia](https://en.wikipedia.org/wiki/OAuth))，像 Amazon、Google、Facebook、Microsoft、Twitter 等公司都透過此機制讓用戶授權給其他網站或應用程式存取他們的資料，同時相關公司也成立 OAuth 討論群組主導這個開放標準的制定。

OAuth 目前最新的版本是 OAuth 2.0，並支援下面4種授權流程：

1. Authorization Code Grant Type Flow

2. Implicit Grant Type Flow

3. Resource Owner Password Credentials Grant Type Flow

4. Client Credentials Grant Type Flow

### Autodesk Forge OAuth 服務

Autodesk Forge 亦透過 OAuth 來保護用戶存放在 Forge 平台上的模型資料及 Autodesk 雲產品 (例如 BIM360、A360、BIM360 Team等) 的數據資料，以及確保有授權的第三方應用程式、網站才可以上傳資料或檔案到 Forge 雲端服務平台上，同時依據使用場景分成下列兩種：

**兩條腿 (2-Legged Context):**

  這種授權場景使用 `Client Credentials Grant Type Flow`  這種授權流程，讓第三方應用程直接與 Forge 平台發出請求以取得存取儲存於 Forge 平台上的資料的權限，其工作流程是：

  1. 你的應用程式呼叫 [POST authenticate](https://forge.autodesk.com/en/docs/oauth/v2/reference/http/authenticate-POST) 端點，並傳入你的 `Client ID` 和 `Client Secret` 以取得 `Access Token`

  2. 取得 `Access Token`後，可以將此 Token 使用在標示 `app only` 或 `user context optional` 的 Forge APIs，例如：

      - [https://forge.autodesk.com/en/docs/data/v2/reference/http/hubs-GET/](https://forge.autodesk.com/en/docs/data/v2/reference/http/hubs-GET/)

      - [https://forge.autodesk.com/en/docs/data/v2/reference/http/buckets-GET/](https://forge.autodesk.com/en/docs/data/v2/reference/http/buckets-GET/)

      - [https://forge.autodesk.com/en/docs/model-derivative/v2/reference/http/job-POST/](https://forge.autodesk.com/en/docs/model-derivative/v2/reference/http/job-POST/)

      - [https://forge.autodesk.com/en/docs/model-derivative/v2/reference/http/urn-manifest-GET/](https://forge.autodesk.com/en/docs/model-derivative/v2/reference/http/urn-manifest-GET/)

      - [https://forge.autodesk.com/en/docs/bim360/v1/reference/http/admin-v1-projects-projectId-users-GET/](https://forge.autodesk.com/en/docs/bim360/v1/reference/http/admin-v1-projects-projectId-users-GET/)

      - [https://forge.autodesk.com/en/docs/bim360/v1/reference/http/field-issues-GET/](https://forge.autodesk.com/en/docs/bim360/v1/reference/http/field-issues-GET/)

**三條腿(2-Legged Context):**

  這種授權場景裡，第三方應用程式需要導引用戶**登入他們的 Autodesk帳號**，此場景拿到的 Access Token 只可以用在標示 `user context required` 或 `user context optional` 的 Forge APIs上，其主要用來存取該帳號放在 Autodesk 雲產品 (例如 BIM360、A360、BIM360 Team、Fusion360 等) 上的數據資料，並可依據換取 Access Token 的方式分為下面兩種：

- Authorization Code Grant Type Flow

  ![](https://developer.doc.autodesk.com/bPlouYTd/245/_images/authorization-code-3-legged-flow.png)

- Implicit Grant Type Flow

  ![](https://developer.doc.autodesk.com/bPlouYTd/245/_images/implicit-3-legged-flow.png)

**Note.** 想要了解上面內容的更多細節可以參考 Autodesk Forge 官網的 [API Basics](https://forge.autodesk.com/en/docs/oauth/v2/developers_guide/basics/)

## Forge 服務簡介及使用示範

// 根據 Work Flow 用 Curl 的方式舉例

![alt Forge Work Flow-1](img/forge-work-flow-1.png)
![alt Forge Work Flow-2](img/forge-work-flow-2.png)

### Data Management API

- 
- Bucket 的命名規則需符合：` [-_.a-z0-9]{3,128}`
- Bucket 類型：會影響上傳到 Bucket 的物件（模型檔案）保存期限
  - transient：檔案會在 24 小時後被自動刪除。
  - temporary：檔案會在 bucket 保存 30 天，時間超過後會自動被刪除。
  - persistent：檔案會永久保存在 bucket 內，直到使用者自行呼叫物件刪除 API 來刪除該物件。

### Model Derivative API



### Design Automation API



### Reality Capture



## Forge SDK 簡介



<br/>

[回到首頁](../README.md)


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

Autodesk Forge 亦透過 OAuth 來保護用戶存放在 Forge 平台上的模型資料及 Autodesk 雲端產品 (例如 BIM360、A360、BIM360 Team、Fusion360 等) 的數據資料，以及確保有授權的第三方應用程式、網站才可以上傳資料或檔案到 Forge 雲端服務平台上，同時依據使用場景分成下列兩種：

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

  這種授權場景裡，第三方應用程式需要導引用戶**登入他們的 Autodesk帳號**，此場景拿到的 Access Token 只可以用在標示 `user context required` 或 `user context optional` 的 Forge APIs上，其主要用來存取該帳號放在 Autodesk 雲端產品 (例如 BIM360、A360、BIM360 Team、Fusion360 等) 上的數據資料，並可依據換取 Access Token 的方式分為下面兩種：

- Authorization Code Grant Type Flow

  ![](https://developer.doc.autodesk.com/bPlouYTd/245/_images/authorization-code-3-legged-flow.png)

- Implicit Grant Type Flow

  ![](https://developer.doc.autodesk.com/bPlouYTd/245/_images/implicit-3-legged-flow.png)



**簡化的流程圖**

![](img/forge-oauth-workflow.png)

**Note.** 想要了解上面內容的更多細節可以參考 Autodesk Forge 官網的 [API Basics](https://forge.autodesk.com/en/docs/oauth/v2/developers_guide/basics/)

## Forge 服務簡介及使用示範

### [Data Management API](https://forge.autodesk.com/en/docs/data/v2/overview/)

Data Management API 提供了一個統一的資料存取模式，用來存取 Autodesk 雲端產品 (例如 BIM360、A360、BIM360 Team、Fusion360 等) 上的資料，以及底層資料存儲服務（OSS，Object Storage Service），依 API 用途簡單分類為下面兩種：

**Data Management API for BIM360:**

主要用來存取 Autodesk 雲端產品 (例如 BIM360、A360、BIM360 Team、Fusion360 等) 上的資料，其功能有：

- 專案存取

  - 取得資料中樞 (Hub) 列表

    ```bash
    curl -v 'https://developer.api.autodesk.com/project/v1/hubs'
    -H 'Authorization: Bearer AuIPTf4KYLTYGVnOHQ0cuolwCW2a'
    ```

  - 取得 Project 列表

    ```bash
    curl -v 'https://developer.api.autodesk.com/project/v1/hubs/b.b1bf0a85-12e7-4a69-b32f-8a57f4459ced/projects'
    -H 'Authorization: Bearer AuIPTf4KYLTYGVnOHQ0cuolwCW2a'
    ```

- 資料夾、檔案版本和關聯檔案

  - 取得上層資料夾

    ```bash
    curl -v 'https://developer.api.autodesk.com/project/v1/hubs/b.b1bf0a85-12e7-4a69-b32f-8a57f4459ced/projects/b.e65d4a5d-3a06-4162-92d7-38c94928a2f7/topFolders' 
    -H 'Authorization: Bearer AuIPTf4KYLTYGVnOHQ0cuolwCW2a'
    ```

  - 取得資料夾內容及檔案版本

    ```bash
    curl -v 'https://developer.api.autodesk.com/project/v1/projects/b.e65d4a5d-3a06-4162-92d7-38c94928a2f7/folders/urn:adsk.wipprod:fs.folder:co.uckWIUa_T9irIZy8R0Swlg/contents'
    -H 'Authorization: Bearer AuIPTf4KYLTYGVnOHQ0cuolwCW2a'
    ```

  - 取得關聯檔案

    ```bash
    curl -v 'https://developer.api.autodesk.com/data/v1/projects/b.e65d4a5d-3a06-4162-92d7-38c94928a2f7/urn:adsk.wipprod:fs.file:vf.Upj7-bcmTKaLhr0yCF30QQ%3Fversion=1/relationships/refs'
    -H 'Authorization: Bearer AuIPTf4KYLTYGVnOHQ0cuolwCW2a'
    ```

  - 搜索、過濾專案和檔案列表

    ```bash
    curl -v 'https://developer.api.autodesk.com/data/v1/projects/b.e65d4a5d-3a06-4162-92d7-38c94928a2f7/folders/urn:adsk.wipprod:fs.folder:co.Wa0ivcArTf2vBsyUJZFs-Q/search?filter[fileType]=rvt'
    -H 'Authorization: Bearer AuIPTf4KYLTYGVnOHQ0cuolwCW2a'
    ```

**OSS (Object Storage Service):**

主要用來上傳/下載檔案及開發者自己的檔案管理，在這個服務裡我們主要面對的是資料容器 (Bucket) 以及容器資料 (Object、上傳的檔案) 的存取，且依 Bucket 的擁有者可以分為下面兩種：

- Autodesk product owned OSS bucket

  Autodesk 雲端產品 (例如 BIM360、A360、BIM360 Team、Fusion360 等) 上所擁有的 bucket，只允許第三方應用程式對於裡面的資料進行有限度的操作。

  - 建立上傳空間

  ```bash
  curl -X POST -H "Content-Type: application/vnd.api+json" -H "Accept: application/vnd.api+json" -H "Authorization: Bearer nFRJxzCD8OOUr7hzBwbr06D76zAT"
  "https://developer.api.autodesk.com/data/v1/projects/b.cGVyc29uYWw6d2l/storage"
  -d '{
        "jsonapi": { "version": "1.0" },
        "data": {
          "type": "objects",
          "attributes": {
            "name": "My First File.jpg"
          },
          "relationships": {
            "target": {
              "data": { "type": "folders", "id": "urn:adsk.wipprod:fs.folder:co.QneBBX7evT2JSrpeQXga0" }
            }
          }
        }
  }'
  ```

  - 上傳檔案

  ```bash
  curl -X PUT -H "Authorization: Bearer nFRJxzCD8OOUr7hzBwbr06D76zAT" --data-binary @D:\SimpleHouse.rvt "https://developer.api.autodesk.com/oss/v2/buckets/wip.dm.prod/objects/2a6d61f2-49df-4d7b.rvt"
  ```

  - 建立版號

  ```bash
  curl -X POST -H "Authorization: Bearer nFRJxzCD8OOUr7hzBwbr06D76zAT" -H "Content-Type: application/vnd.api+json" -H "Accept: application/vnd.api+json"
  "https://developer.api.autodesk.com/data/v1/projects/b.cGVyc29uYWw6d2l/items" -d '{
      "jsonapi": { "version": "1.0" },
      "data": {
        "type": "items",
        "attributes": {
          "displayName": "SimpleHouse.rvt",
          "extension": {
            "type": "items:autodesk.bim360:File",
            "version": "1.0"
          }
        },
        "relationships": {
          "tip": {
            "data": {
              "type": "versions", "id": "1"
            }
          },
          "parent": {
            "data": {
              "type": "folders",
              "id": "urn:adsk.wipprod:fs.folder:co.BJU3PTc4Sd2CmXM492XUiA"
            }
          }
        }
      },
      "included": [
        {
          "type": "versions",
          "id": "1",
          "attributes": {
            "name": "SimpleHouse.rvt",
            "extension": {
              "type": "versions:autodesk.bim360:File",
              "version": "1.0"
            }
          },
          "relationships": {
            "storage": {
              "data": {
                "type": "objects",
                "id": "urn:adsk.objects:os.object:wip.dm.prod/2a6d61f2-49df-4d7b.rvt"
              }
            }
          }
        }
      ]
    }'
  ```

- Developer managed OSS bucket (**本次學習目標**)

  此為第三方應用程式所擁有的 bucket，這種資料容器是由 Forge 平台的用戶自己透過 [POST buckets](https://forge.autodesk.com/en/docs/data/v2/reference/http/buckets-POST/) 端點建立的 bucket，平台用戶對於 bucket 有較多限度的操作，例如透過 [PUT Object](https://forge.autodesk.com/en/docs/data/v2/reference/http/buckets-:bucketKey-objects-:objectName-PUT/) 直接上傳模型檔案到 bucket 裡。

  - 建立 Bucket

    ```bash
    curl -v "https://developer.api.autodesk.com/oss/v2/buckets"
      -X POST
      -H "Content-Type: application/json"
      -H "Authorization: Bearer kgEJWMJitdYbhfxghap8SbZqXMoS"
      -d '
      {
        "bucketKey":"bucketExamplekey",
        "policyKey":"transient"
      }
      '
    ```

  - 上傳模型檔案

    ```bash
    curl -v 'https://developer.api.autodesk.com/oss/v2/buckets/mybucket/objects/SimpleHouse.rvt'
    -X 'PUT'
    -H 'Authorization: Bearer AlmsGlZlqz1JkkzEruUdINMKA6IF'
    -H 'Content-Type: application/octet-stream'
    -T 'SimpleHouse.rvt'
    ```

  - 下載檔案

    ```bash
    curl -v "https://developer.api.autodesk.com/oss/v2/buckets/mybucket/objects/SimpleHouse.rvt"
    -X GET
    -H "Authorization: Bearer ShiAeQ67rdNSfmyEmtGW8Lnrcqto"
    ```

### [Model Derivative API](https://forge.autodesk.com/en/docs/model-derivative/v2/overview/) (**本次學習目標**)

Model Derivative API 支援將近 60 餘種業界常見的模型格式、檔案轉檔為其他格式，和截取檔案中的模型資料、清單文件，其功能包含：

- 將 二維(2D) 或 三維(3D) 模型檔案轉檔成網頁、行動裝置能瀏覽的格式 (Autodesk Forge Viewer 的 SVF、F2D 格式)

-將部份支援檔案從原始格式轉檔成一些通用格式，例如 STL、STEP、.IGES 及 OBJ 等
- 截取模型的階層結構、元件屬性

- 建立不同尺寸的模型縮圖

- Revit 匯出成 IFC


![](https://developer.doc.autodesk.com/bPlouYTd/245/_images/MD-overview-diagram.png)

### [BIM360 API](https://forge.autodesk.com/en/docs/bim360/v1/overview/)

前面提到的 [Data Management API](#data-management-api) 是用來管理模型檔案資料而存在的 API，而BIM360 API 是專門用來管理、存取 BIM360 軟體平台資料存在的 API，其功能包含：

- Account Admin (**H**ead **Q**uarter) API: 用來進行BIM360 帳務管理相關作業（如專案、公司及人員等）的 API

- Issues API: 用來在 `Document Management模組` 和 `Field Management模組` 進行議題管理的 API

- Checklists API: 用來在 `Field Management模組` 進行文件議題管理的 API

- Document Management API: 用來在 `Document Management模組` 進行資料夾權限管理、匯出 PDF 等作業的 API

- Cost Management API: 用來在 `Cost Management模組` 進行工程預算、花費、合約等管理的 API

- Model Coordination API: 用來在 `Model Coordination模組` 進行模型協調作業 (如碰撞檢討等) 管理 的 API

![](img/bim360-cde.png)

### [Design Automation API](https://forge.autodesk.com/en/docs/design-automation/v3/overview/)

Design Automation API 是一組可以用來協助設計自動化流程的 API，可以想像成 Autodesk 把自己的設計軟體如 AutodCAD, Revit, Inventor 和 3ds Max 等放在雲端，讓使用者在不用安裝、開啟相關軟體的情況下也能體驗到相關軟體帶來的好處；以 Revit 為例，我們可以透過 Design Automation API for Revit 做到：

- 雲端建立 RFA、RVT 檔，或是條件式的產生自定的內容
- 雲上修改 Revit 模型的內容
- 將 Revit 模型裡的資料倒出來，或是截取部份資料

![](https://developer-dev.static.autodesk.com/coverpage_images/da.svg)

### [Reality Capture API](https://forge.autodesk.com/en/docs/reality-capture/v1/developers_guide/overview/)

Reality Capture API 是一組用於照片建模 API，支援將空拍機或是手提攝影機所產出的照片處理成點雲、3D Meshes 和正射影相。

![](https://developer-dev.static.autodesk.com/coverpage_images/rc3.gif)

### [Viewer API](https://forge.autodesk.com/en/docs/viewer/v7/overview/)  (**本次學習目標**)

Forge Viewer 又稱 **L**arge **M**odel **V**iewer，是基於 [three.js](https://threejs.org/) 開發的 JavaScript 程式庫，可以用來在網頁裡瀏覽、檢視、協作多種二維 (2D) 或三維 (3D) 的模型，並開放豐富的應用介面 (API) 來發展、擴充自有應用，其功能包含：

- 網頁式無外掛瀏覽，支援行動裝置的瀏覽器
- 剖切檢視、爆炸檢視、量測、漫遊
- 取得構件屬性或參數
- 豐富的擴充模組
- 搜尋、標記
- 圖紙超連結

**3D模型**

![](https://developer.doc.autodesk.com/bPlouYTd/249/_images/design3d5.jpg)

**2D模型**

![](https://developer.doc.autodesk.com/bPlouYTd/249/_images/design2d5.jpg)

#### Viewer 前處理工作流程圖

![alt Forge Viewer Work Flow](img/forge-viewer-workflow.png)

#### Viewer 前處理工作流程 API呼叫範例

1. 取得權杖 (Access Token)

    ```bash
    curl -v 'https://developer.api.autodesk.com/authentication/v1/authenticate'
      -X 'POST'
      -H 'Content-Type: application/x-www-form-urlencoded'
      -d '
        client_id=YOUR_FORGE_CLIENT_ID&
        client_secret=YOUR_FORGE_CLIENT_SECRETE&
        grant_type=client_credentials&
        scope=viewable:read
      '
    ```

2. 上傳模型

    ```bash
    curl -v 'https://developer.api.autodesk.com/oss/v2/buckets/YOUR_BUCKET_NAME/objects/adsk-forge-helloworld.rvt'
      -X 'PUT'
      -H 'Authorization: Bearer YOUR_FORGE_ACCESS_TOKEN'
      -H 'Content-Type: application/octet-stream'
      -T 'adsk-forge-helloworld.rvt'
    ```

3. 送出轉檔工作

    ```bash
    curl -X 'POST' \
        -H 'Content-Type: application/json; charset=utf-8' \
        -H 'Authorization: Bearer YOUR_FORGE_ACCESS_TOKEN'
        -v 'https://developer.api.autodesk.com/modelderivative/v2/designdata/job' \
        -d
          '{
            "input": {
              "urn": "dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6WU9VUl9CVUNLRVRfTkFNRS9hZHNrLWZvcmdlLWhlbGxvd29ybGQucnZ0"
            },
            "output": {
              "formats": [
                {
                  "type": "svf",
                  "views": [
                    "2d",
                    "3d"
                  ]
                }
              ]
            }
          }'
    ```

4. 取得轉檔進度

    ```bash
    curl -X 'GET' \
        -H 'Authorization: Bearer YOUR_FORGE_ACCESS_TOKEN' \
        -v 'https://developer.api.autodesk.com/modelderivative/v2/designdata/dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6WU9VUl9CVUNLRVRfTkFNRS9hZHNrLWZvcmdlLWhlbGxvd29ybGQucnZ0/manifest'
    ```

## Forge Client SDK 簡介

除了上面提到的使用 `curl` 命令列工具 (**Command-line interface，CLI**) 的方式外，還可以透過各程式語言的 **HTTP client** 來呼叫 Forge 平台的 (REST style) Web API，且為了方便開發人員快速的整合 Forge REST API 到你的應用程式裡，針對不同程式語言提供了 `Forge Client SDK` 。

### 支援的 Client SDK 套件

- .NET SDK: <https://github.com/Autodesk-Forge/forge-api-dotnet-client>  (**本次學習目標**)
- Node.js SDK: <https://github.com/Autodesk-Forge/forge-api-nodejs-client>
- PHP SDK: <https://github.com/Autodesk-Forge/forge-php-client>
- Java SDK: <https://github.com/Autodesk-Forge/forge-api-java-client>

### .NET SDK 使用範例 (以**Viewer 前處理工作流程**為例)

1.取得權杖 (Access Token)

  ```c#
    var scopes = new Scope[] {
      Scope.DataRead,
      Scope.DataWrite,
      Scope.DataCreate
    };
    var oauth = new TwoLeggedApi();
    string grantType = "client_credentials";

    dynamic bearer = await oauth.AuthenticateAsync(
      "YOUR_FORGE_CLIENT_ID",
      "YOUR_FORGE_CLIENT_SECRET",
      grantType,
      scopes
    );
  ```

2.上傳模型

  ```c#
  var objects = new ObjectsApi();
  objects.Configuration.AccessToken = bearer.access_token;

  dynamic uploadedObj;
  using( StreamReader streamReader = new StreamReader( fileSavePath ) )
  {
    uploadedObj = await objects.UploadObjectAsync(
      "YOUR_BUCKET_NAME",
      "adsk-forge-helloworld.rvt",
      (int)streamReader.BaseStream.Length,
      streamReader.BaseStream,
      "application/octet-stream"
    );
  }
  ```

3.送出轉檔工作

  ```c#
  List<JobPayloadItem> outputs = new List<JobPayloadItem>()
  {
    new JobPayloadItem(
      JobPayloadItem.TypeEnum.Svf,
      new List<JobPayloadItem.ViewsEnum>()
      {
        JobPayloadItem.ViewsEnum._2d,
        JobPayloadItem.ViewsEnum._3d
      }
    )
  };

  var job = new JobPayload(
    new JobPayloadInput( "dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6WU9VUl9CVUNLRVRfTkFNRS9hZHNrLWZvcmdlLWhlbGxvd29ybGQucnZ0" ),
    new JobPayloadOutput( outputs )
  );

  // start the translation
  var derivative = new DerivativesApi();
  derivative.Configuration.AccessToken = bearer.access_token;
  dynamic jobPosted = await derivative.TranslateAsync(job);
  ```

4.取得轉檔進度

  ```c#
  var derivative = new DerivativesApi();
  derivative.Configuration.AccessToken = bearer.access_token;
  dynamic manifest = derivative.GetManifest( "dXJuOmFkc2sub2JqZWN0czpvcy5vYmplY3Q6WU9VUl9CVUNLRVRfTkFNRS9hZHNrLWZvcmdlLWhlbGxvd29ybGQucnZ0" );
  ```

<br/>

[回到首頁](../README.md)
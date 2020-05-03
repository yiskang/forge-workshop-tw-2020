# 章節四 Forge OAuth、Forge 服務整體及 SDK 簡介

## Forge OAuth



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


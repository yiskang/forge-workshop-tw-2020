# 章節六 Forge 模型轉檔及進度查詢章節自主練習

## 練習目標

1. 前端實作 ForgeTree.js，並完成下列功能
   - 實作 ForgeTree.js 透過  [jstree.js](https://www.jstree.com/) 右鍵選單送出所選取物件（模型檔案）的轉檔工作
   - 實作 ForgeTree.js 透過  [jstree.js](https://www.jstree.com/) 查詢所選取物件的轉檔進度
2. 後端實作下列功能：
   - 透過 Forge .NET Client SDK 的 `DerivativesApi` 實作送出物件（模型檔案）轉檔工作的端點： `POST /api/forge/modelderivative/jobs`
   - 查詢轉檔工作：`GET https://developer.api.autodesk.com/modelderivative/v2/designdata/{urn}/manifest`

## 示範及說明影片

1. Learn Forge 模型轉檔及轉檔進度查詢前端功能實作（jstree）<br/>

[![](http://img.youtube.com/vi/_E9f-ZO6CJs/0.jpg)](http://www.youtube.com/watch?v=_E9f-ZO6CJs "6.1-Frontend Model Translation and Progess Check")

2. Learn Forge 模型轉檔及轉檔進度查詢後端功能實作<br/>

[![](http://img.youtube.com/vi/uf3esry6b-k/0.jpg)](http://www.youtube.com/watch?v=uf3esry6b-k "6.2-Backend Model Translation and Progess Check")

## 參考資料

 - [章節講議](README.md)
 - 使用到的 Forge APIs
    - https://forge.autodesk.com/en/docs/model-derivative/v2/reference/http/job-POST/
    - https://forge.autodesk.com/en/docs/model-derivative/v2/reference/http/urn-manifest-GET/

<br/>

[回到首頁](../README.md)
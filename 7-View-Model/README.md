# 章節七 Forge 模型檢視

## Forge Viewer 簡介

### Forge Viewer 技術簡易架構

![alt ForgeViewerTech](img/forge-viewer-tech.png)

### Forge Viewer 實作

- 1.實作 `launchViewer( urn )`

  - ```javascript
    var viewer;

    function launchViewer(urn) {
    }
    ```

- 2.初始化 Viewer

  - ```javascript
    function getForgeToken(callback) {
      fetch('/api/forge/oauth/token').then(res => {
        res.json().then(data => {
          callback(data.access_token, data.expires_in);
        });
      });
    }

    var options = {
      env: 'AutodeskProduction',
      getAccessToken: getForgeToken
    };

    Autodesk.Viewing.Initializer(options, () => {
      var htmlDiv = document.getElementById( 'forgeViewer' );
      viewer = new Autodesk.Viewing.GuiViewer3D( htmlDiv, { extensions: [ 'Autodesk.DocumentBrowser'] });

      viewer.start();
      var documentId = 'urn:' + urn;

      // Read model vies code goes here
    });
    ```

- 3.讀取模型視圖 Manifest（可載入的模型視圖）

  - ```javascript
    Autodesk.Viewing.Document.load(
      documentId,
      onDocumentLoadSuccess,
      onDocumentLoadFailure
    );

    function onDocumentLoadSuccess(viewerDocument) {
      // Load model code goes here
    }

    function onDocumentLoadFailure() {
        console.error('Failed fetching Forge manifest');
    }
    ```

- 4.載入模型視圖（Viewable Bubble）

  - ```javascript
    var defaultModel = viewerDocument.getRoot().getDefaultGeometry();
    viewer.loadDocumentNode(viewerDocument, defaultModel);
    ```

## 章節自主練習

[點我進入練習](Practice.md)

<br/>

[回到首頁](../README.md)
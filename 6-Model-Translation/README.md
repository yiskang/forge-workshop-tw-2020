# 章節六 Forge 模型轉檔及進度查詢

## Learn Forge 模型轉檔及進度查詢功能簡介

### 模型轉檔

- 前端
  
  - ```javascript
    function translateObject(node) {
      $("#forgeViewer").empty();
      if (node == null) node = $('#appBuckets').jstree(true).get_selected(true)[0];
      var bucketKey = node.parents[0];
      var objectKey = node.id;
      jQuery.post({
        url: '/api/forge/modelderivative/jobs',
        contentType: 'application/json',
        data: JSON.stringify({ 'bucketKey': bucketKey, 'objectName': objectKey }),
        success: function (res) {
          $("#forgeViewer").html('Translation started! Please try again in a moment.');
        },
      });
    }
    ```
- 後端
  
  - ```c#
    /// <summary>
    /// Start the translation job for a give bucketKey/objectName
    /// </summary>
    /// <param name="objModel"></param>
    /// <returns></returns>
    [HttpPost]
    [Route("api/forge/modelderivative/jobs")]
    public async Task<dynamic> TranslateObject([FromBody]TranslateObjectModel objModel)
    {
        dynamic oauth = await OAuthController.GetInternalAsync();
    
        // prepare the payload
        List<JobPayloadItem> outputs = new List<JobPayloadItem>()
        {
        new JobPayloadItem(
            JobPayloadItem.TypeEnum.Svf,
            new List<JobPayloadItem.ViewsEnum>()
            {
            JobPayloadItem.ViewsEnum._2d,
            JobPayloadItem.ViewsEnum._3d
            })
        };
        JobPayload job;
        job = new JobPayload(new JobPayloadInput(objModel.objectName), new JobPayloadOutput(outputs));
    
        // start the translation
        DerivativesApi derivative = new DerivativesApi();
        derivative.Configuration.AccessToken = oauth.access_token;
        dynamic jobPosted = await derivative.TranslateAsync(job);
        return jobPosted;
    }
    ```

### 轉檔進度查詢

- 前端
  
  - ```javascript
    $('#appBuckets').jstree().bind("activate_node.jstree", function (evt, data) {
        if (data != null && data.node != null && data.node.type == 'object') {
          $("#forgeViewer").empty();
          var urn = data.node.id;
          getForgeToken(function (access_token) {
            jQuery.ajax({
              url: 'https://developer.api.autodesk.com/modelderivative/v2/designdata/' + urn + '/manifest',
              headers: { 'Authorization': 'Bearer ' + access_token },
              success: function (res) {
                if (res.status === 'success') launchViewer(urn);
                else $("#forgeViewer").html('The translation job still running: ' + res.progress + '. Please try again in a moment.');
              },
              error: function (err) {
                var msgButton = 'This file is not translated yet! ' +
                  '<button class="btn btn-xs btn-info" onclick="translateObject()"><span class="glyphicon glyphicon-eye-open"></span> ' +
                  'Start translation</button>'
                $("#forgeViewer").html(msgButton);
              }
            });
          })
        }
      });

      function autodeskCustomMenu(autodeskNode) {
      var items;

      switch (autodeskNode.type) {

          // ...

          case "object":
            items = {

                // ...

                translateFile: {
                    label: "Translate",
                    action: function () {
                        var treeNode = $('#appBuckets').jstree(true).get_selected(true)[0];
                        translateObject(treeNode);
                    },
                    icon: 'glyphicon glyphicon-eye-open'
                }
            };
            break;
      }

      return items;
    }
    ```

## 章節自主練習

[點我進入練習](Practice.md)

<br/>

[回到首頁](../README.md)
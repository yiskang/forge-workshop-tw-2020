# Autodesk Forge基礎訓練工作坊

對3/5 Forge 開發基礎專題的實作專題意猶未盡嗎？或是依舊對 Autodesk Forge摸不著頭緒、不知道如何下手呢？本次線上課程將延續『Forge viewer 案例從搭建到部署』實作專題，並為六月份的 Forge 加速器活動做暖身，在兩天的時間內使用 Learn Forge 官方範例，手把手帶大家建個人第一個 Forge Viewer 應用！

## 活動目標及預期成果

活動期間將帶領大家依照 [Learn Forge](https://learnforge.autodesk.io/#/) 的學習路線，並使用 **[ASP.NET Core](https://docs.microsoft.com/zh-tw/aspnet/core/?view=aspnetcore-3.1)** 這個技術一步一步的完成自己的第一個 Forge Viewer 網頁應用程式，最後成果會長的像下圖：

![alt "Website layout"](5-Bucket-Management/img/frontend-layout-setup.png)

## 活動議程

<style>
	ul {
		padding: 15px;
	}
</style>
<script>
(function() {
	function docReady( fn ) {
			// see if DOM is already available
			if( document.readyState === 'complete' || document.readyState === 'interactive' ) {
			// call on next available tick
			setTimeout( fn, 1 );
		} else {
			document.addEventListener( 'DOMContentLoaded', fn );
		}
	}

	docReady(function() {
		document.querySelectorAll( 'a.self-practice' ).forEach(function( a ) {
			a.href = a.href.replace( '.md', '.html' );
		});
	});
})();
</script>

#### Day1
<table width="604">
	<tbody>
		<tr>
			<td width="150">
				<p>時間</p>
			</td>
			<td width="293">
				<p>內容</p>
			</td>
			<td width="189">
				<p>內容型式</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>09:00 &ndash; 09:10</p>
			</td>
			<td width="293">
				<p>章節一：</p>
				<p>l&nbsp;&nbsp; 活動開場、簡介</p>
				<p>l&nbsp;&nbsp; Forge 開發者帳號建立及註冊</p>
			</td>
			<td width="189">
				<p>講師簡報導說(<a href="1-Register">講議連結</a>)</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>09:10-09:30</p>
			</td>
			<td width="293">
				<p>章節一自我學習</p>
			</td>
			<td width="189">
				<ul>
					<li>提供示範影片自學</li>
					<li>隨時Slack發問</li>
					<li>需要時可Zoom視訊答疑</li>
					<li><a class="self-practice" href="1-Register/Practice.md">自主練習連結</a></li>
				</ul>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>09:30-09:40</p>
			</td>
			<td width="293">
				<p>章節一答疑</p>
			</td>
			<td width="189">
				<p>Zoom答疑</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>09:40-09:50</p>
			</td>
			<td width="293">
				<p>章節二：</p>
				<p>l&nbsp;&nbsp; Learn Forge網站簡介</p>
				<p>l&nbsp;&nbsp; Learn Forge開發專案基本設定</p>
			</td>
			<td width="189">
				<p>講師簡報導說(<a href="2-Setup">講議連結</a>)</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>09:50-10:30</p>
			</td>
			<td width="293">
				<p>章節二自我學習</p>
			</td>
			<td width="189">
				<ul>
					<li>提供示範影片自學</li>
					<li>隨時Slack發問</li>
					<li>需要時可Zoom視訊答疑</li>
					<li><a class="self-practice" href="2-Setup/Practice.md">自主練習連結</a></li>
				</ul>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>10:30-10:40</p>
			</td>
			<td width="293">
				<p>章節二答疑</p>
			</td>
			<td width="189">
				<p>Zoom答疑</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>10:40-11:00</p>
			</td>
			<td width="293">
				<p>中場休息</p>
			</td>
			<td width="189">
				<p>-</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>11:00-11:10</p>
			</td>
			<td width="293">
				<p>章節三：</p>
				<p>l&nbsp;&nbsp; Forge Viewer 初始化步驟簡介</p>
				<p>l&nbsp;&nbsp; Forge Viewer基本功能介紹</p>
			</td>
			<td width="189">
				<p>講師簡報導說(<a href="3-ForgeViewerBasic">講議連結</a>)</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>11:10-11:50</p>
			</td>
			<td width="293">
				<p>章節三自我學習</p>
			</td>
			<td width="189">
				<ul>
					<li>提供示範影片自學</li>
					<li>隨時Slack發問</li>
					<li>需要時可Zoom視訊答疑</li>
					<li><a class="self-practice" href="3-ForgeViewerBasic/Practice.md">自主練習連結</a></li>
				</ul>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>11:50-12:00</p>
			</td>
			<td width="293">
				<p>章節三答疑</p>
			</td>
			<td width="189">
				<p>Zoom答疑</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>12:00-14:00</p>
			</td>
			<td width="293">
				<p>中場休息</p>
			</td>
			<td width="189">
				<p>-</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>14:00-14:20</p>
			</td>
			<td width="293">
				<p>章節四：</p>
				<p>l&nbsp;&nbsp; Forge OAuth驗證</p>
				<p>l&nbsp;&nbsp; Forge 服務簡介及使用示範</p>
				<p>l&nbsp;&nbsp; Forge SDK簡介</p>
			</td>
			<td width="189">
				<p>講師簡報導說(<a href="4-OAuth-SDK">講議連結</a>)</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>14:20-14:30</p>
			</td>
			<td width="293">
				<p>章節四答疑</p>
			</td>
			<td width="189">
				<p>Zoom答疑</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>14:30-14:40</p>
			</td>
			<td width="293">
				<p>章節五：</p>
				<p>l&nbsp;&nbsp; Forge Data Management - Bucket新增及模型上傳</p>
				<p>l&nbsp;&nbsp; 下載及刪除已上傳模型檔案</p>
			</td>
			<td width="189">
				<p>講師簡報導說(<a href="5-Bucket-Management">講議連結</a>)</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>14:40-15:30</p>
			</td>
			<td width="293">
				<p>章節五自我學習</p>
			</td>
			<td width="189">
				<ul>
					<li>提供示範影片自學</li>
					<li>隨時Slack發問</li>
					<li>需要時可Zoom視訊答疑</li>
					<li><a class="self-practice" href="5-Bucket-Management/Practice.md">自主練習連結</a></li>
				</ul>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>15:30-15:40</p>
			</td>
			<td width="293">
				<p>章節五答疑</p>
			</td>
			<td width="189">
				<p>Zoom答疑</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>15:40-16:00</p>
			</td>
			<td width="293">
				<p>中場休息</p>
			</td>
			<td width="189">
				<p>-</p>
			</td>
		</tr>
	</tbody>
</table>



#### Day 2
<table width="604">
	<tbody>
		<tr>
			<td width="150">
				<p>時間</p>
			</td>
			<td width="293">
				<p>內容</p>
			</td>
			<td width="189">
				<p>內容型式</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>09:00-09:20</p>
			</td>
			<td width="293">
				<p>章節六：</p>
				<p>l&nbsp;&nbsp; Forge Model Derivative - 模型轉檔</p>
			</td>
			<td width="189">
				<p>講師簡報導說(<a href="6-Model-Translation">講議連結</a>)</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>09:20-10:10</p>
			</td>
			<td width="293">
				<p>章節六自我學習</p>
			</td>
			<td width="189">
				<ul>
					<li>提供示範影片自學</li>
					<li>隨時Slack發問</li>
					<li>需要時可Zoom視訊答疑</li>
					<li><a class="self-practice" href="6-Model-Translation/Practice.md">自主練習連結</a></li>
				</ul>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>10:10-10:20</p>
			</td>
			<td width="293">
				<p>章節六答疑</p>
			</td>
			<td width="189">
				<p>Zoom答疑</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>10:20 – 10:30</p>
			</td>
			<td width="293">
				<p>中場休息</p>
			</td>
			<td width="189">
				<p>-</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>10:30 – 10:40</p>
			</td>
			<td width="293">
				<p>章節七：</p>
				<p>l   Forge Viewer 實作</p>
			</td>
			<td width="189">
				<p>講師簡報導說(<a href="7-View-Model">講議連結</a>)</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>10:40-11:50</p>
			</td>
			<td width="293">
				<p>章節七自我學習</p>
			</td>
			<td width="189">
				<ul>
					<li>提供示範影片自學</li>
					<li>隨時Slack發問</li>
					<li>需要時可Zoom視訊答疑</li>
					<li><a class="self-practice" href="7-View-Model/Practice.md">自主練習連結</a></li>
				</ul>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>11:50-12:00</p>
			</td>
			<td width="293">
				<p>章節七答疑</p>
			</td>
			<td width="189">
				<p>Zoom答疑</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>12:00-14:00</p>
			</td>
			<td width="293">
				<p>中場休息</p>
			</td>
			<td width="189">
				<p>-</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>14:00-15:50</p>
			</td>
			<td width="293">
				<p>章節八：</p>
				<p>l   Forge Viewer 功能及API示範</p>
			</td>
			<td width="189">
				<p>講師簡報導說，並讓學員跟著講師練習(<a href="8-Viewer-APIs">講議連結</a>)</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>15:50-16:00</p>
			</td>
			<td width="293">
				<p>章節八答疑</p>
			</td>
			<td width="189">
				<p>Zoom答疑</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>16:00-16:10</p>
			</td>
			<td width="293">
				<p>中場休息</p>
			</td>
			<td width="189">
				<p>-</p>
			</td>
		</tr>
		<tr>
			<td width="150">
				<p>16:10-17:10</p>
			</td>
			<td width="293">
				<p>Forge 應用需求的技術討論和程式碼分析</p>
			</td>
			<td width="189">
				<p>-</p>
			</td>
		</tr>
	</tbody>
</table>

## 必備知識

曾接觸過網頁（前端/後端）應用程式開發、設計等經驗，具 ASP.NET Core網頁程式開發經驗者尤佳。

## 課前準備

1. 事先安裝好下列軟體設定開發環境：
   - Visual Studio、Visual Studio for Mac 或 Visual Studio Code（含[C#擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)）
   - [.NET Core SDK 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1)

2. 確保網路連線順暢、並可以存取：
   - Forge 相關網域，如 [Autodesk Forge](https://forge.autodesk.com/) 及 [Forge RCDB](https://forge-rcdb.autodesk.io/configurator?id=57f3739777c879f48ad54a44)（**請確保能夠成功開啟**）
   - [Slack](https://slack.com/) 及 [Zoom](https://zoom.us/test) (**於報名成功後會收到 Slack 邀請**)
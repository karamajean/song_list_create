# song_list_create

是的，你可以使用 Node.js 與 Spotify Web API 進行交互。以下是一個基本的例子，展示如何使用 Node.js 和 "spotify-web-api-node" 套件來創建一個新的 Spotify 歌單：

首先，你需要安裝 "spotify-web-api-node" 套件。在你的命令行介面中，輸入以下命令：

bash

npm install spotify-web-api-node
然後，你可以在你的 Node.js 應用程序中使用以下程式碼：

javascript

var SpotifyWebApi = require('spotify-web-api-node');

// 設定你的應用的認證資訊
var spotifyApi = new SpotifyWebApi({
  clientId: 'your-client-id',
  clientSecret: 'your-client-secret',
  redirectUri: 'your-redirect-uri'
});

// 獲得一個 access token
spotifyApi.clientCredentialsGrant().then(
  function(data) {
    spotifyApi.setAccessToken(data.body['access_token']);

    // 創建一個新的歌單
    spotifyApi.createPlaylist('your-username', 'My New Playlist', { 'public' : false })
      .then(function(data) {
        console.log('Created playlist!');
      }, function(err) {
        console.log('Something went wrong!', err);
      });
  },
  function(err) {
    console.log('Something went wrong when retrieving an access token', err);
  }
);

請注意，你需要將 'your-client-id'、'your-client-secret'、'your-redirect-uri' 和 'your-username' 替換為你的實際值。

這只是一個基本的例子，你可能需要根據你的具體需求進行調整。你應該參考 "spotify-web-api-node" 的官方文檔，以獲得更詳細的資訊和範例程式碼。

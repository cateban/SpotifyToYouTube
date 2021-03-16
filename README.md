# Transfering Spotify playlist to YouTube



With the following code, you will be able to transfer a playlist from Spotify to Youtube. 



Make sure that you already have the following, you will need it.

- App  in https://developer.spotify.com/dashboard/ 
- Project in https://console.cloud.google.com/projectcreate/ with YouTube Data API enabled, API Key Enabled & OAuth 2.0 Client IDs.

- client_secret.json (you get it in the OAuth 2.0 Client IDs (inside the Google Cloud Console) )
- api_key (inside the Google Cloud Console)
- client_id & client_secret (inside Spotify Developer Platform)





Basically, the code does the following:

- Authenticate to YouTube
  - For this, you will need to have a .json file with some credentials. You get this json file on the console of your application when you enable OAuth 2.0 authentication. (You need to get into the user in order to manage its playlists.)
- Authenticate to Spotify
  - You have to pass the client_id & client_secret that you get on Spotify's developer platform when you create your app. (Playlists should be public because we are not requiring user authentication. Also, make sure that the redirect_uri="https://www.spotify.com/mx/home/" is on your apps whitelist in Spotify Developer Platform). 
- Get all tracks of a given user & playlist_id and parse them into strings. 
- Loop the strings you just made into the YouTube API to search and get the video id of the first result (hopefully, the first result will always be the best/official version of the song). 
- Insert that video id into a playlist in YouTube.





## Limitations

YouTube's API gives you a total of 10,000 units. So a search request is 100 units and an insert request is 50 units. 

If your playlist has too many songs it won't be possible to make the transfer in a single run but we will have to make some mods.

Since the inserting into YouTube's playlist needs a list of video_ids to insert. There is also a [selenium_videoid.ipynb](https://github.com/cateban/SpotifyToYoutube/blob/main/selenium_videoid.ipynb) that you can use to scrap the results of the Spotify response and extract the video id from the url of the first result and not waste those precious units.


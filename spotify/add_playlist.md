# Adding a new playlist through the spotify API

The spotify API makes possible to easily create new playlist via simple api requests.

Here i will focus on the request and the response returned by the api.

## The request.
The API expects a **POST** request with a **QAuth Token** to this specific endpoint : ```https://api.spotify.com/v1/users/{user_id}/playlists``` where ``` user_id``` is the username that can be find in **Account** section.

<img src='https://user-images.githubusercontent.com/90383672/208451178-e3c6e478-3fd1-4b36-a762-2e97d44947f8.png' width = 300  />

You can get a QAuth Token from [here](https://developer.spotify.com/console/post-playlists/).




the body of the request should contain following fields:

- **name(string)** : the name of the new playlist
- **public(bool)** : a boolean value for if the playlist should be public or private
- **collaborative(bool)** : a boolean value for if the playlist should be collaborative or not.
- **description(string)** : a description for the playlist 

### A python example

An python mplementation of that request :

```python
import requests

ENDPOINT = 'https://api.spotify.com/v1/users/{user_id}/playlists'
QAUTH_TOKEN = '******BQDT4Vv2d_h9dpdW*****'

class Client():
	def __init__(self,URL, ACCESS_TOKEN):
		self.URL = URL 
		self.ACCESS_TOKEN = ACCESS_TOKEN

	def new_playlist(self, name, description,public, collaborative):
		response = requests.post(
			self.URL,
			headers = 
                {
                "Authorization" : f"Bearer {self.ACCESS_TOKEN}"
			    },
			json = 
                {
                "name":name ,
                "description" : description,
                "public":public, 
                "collaborative" : collaborative
		        })
  
		json_resp = response.json()
		return json_resp

client = Client(ENDPOINT, QAUTH_TOKEN)
name = 'My New Playlist'
description = 'Created through spotify API'
public = False
collaborative = False


new_playlist = client.new_playlist(name, description, public, collaborative)
print(new_playlist)
  

```

<img src='https://user-images.githubusercontent.com/90383672/208456265-e5b09851-847e-4f71-b509-eee7768d589a.png'  width=500/>


The Playlist is successfully created .
The API return a Playlist object containing details about the playlist.


References : 
- [Spotify For Developers - Web Api Reference](https://developer.spotify.com/documentation/web-api/reference/#/operations/create-playlist)
- [Create Playlist - Spotify For developers](https://developer.spotify.com/console/post-playlists/)







# List user's playlists trough the spotify API.

The spotify API makes possible to easily get a user's  playlist via simple api requests.

Here i will focus on the request and the response returned by the api.

## The request.
The API expects a **POST** request with a **QAuth Token** to this specific endpoint : ```https://api.spotify.com/v1/users/{user_id}/playlists``` where ``` user_id``` is the username that can be find in **Account** section.

<img src='https://user-images.githubusercontent.com/90383672/208451178-e3c6e478-3fd1-4b36-a762-2e97d44947f8.png' width = 300  />

You can get a QAuth Token from [here](https://developer.spotify.com/console/post-playlists/).

the query of the request should contain :

- **limit(int)** : The maximum number of items to return
- **offset(int)** : The index of the first playlist to return

### A python example

An python mplementation of that request :
```python

import requests
from prettytable import PrettyTable
table = PrettyTable()
play_list = []

ENDPOINT = 'https://api.spotify.com/v1/users/{user_id}/playlists'
QAUTH_TOKEN = '*****dcsbrrnmMUaswPpZnW*******'

class Client():
	def __init__(self,URL, ACCESS_TOKEN):
		self.URL = URL 
		self.ACCESS_TOKEN = ACCESS_TOKEN

	def list_playlists(self, limit, offset):
		#list the current user's playlists
		response = requests.get(
			self.URL,
			headers= {
				"Authorization" : f"Bearer {self.ACCESS_TOKEN}",
				"offset" : offset,
				"limit" : limit
			})
		json_resp = response.json()
		return json_resp

client = Client(ENDPOINT, QAUTH_TOKEN)

limit = '20'
offset = '0'

table.field_names = ['Name', "No of songs"]
playlist_items = client.list_playlists(limit, offset)

for item in playlist_items['items']:
    play_list.append(item)
    table.add_row([item['name'], item['tracks']['total']])
print(table)

```

Result :

                                                  +--------------+-------------+
                                                  |     Name     | No of songs |
                                                  +--------------+-------------+
                                                  | new playlist |      5      |
                                                  |     sudo     |      4      |
                                                  |   Népal 🔥   |      10     |
                                                  |     Play     |      42     |
                                                  |      •       |      17     |
                                                  +--------------+-------------+



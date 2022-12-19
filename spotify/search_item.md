# Search for a song , an album , an artist trough spotify API

The spotify API makes possible to easily search for an item(song, album, artist,playlist) via simple api requests.

Here i will focus on the request and the response returned by the api.

## The request.
The API expects a **POST** request with a **QAuth Token** to this specific endpoint : ```https://api.spotify.com/v1/search``` 

You can get a QAuth Token from [here](https://developer.spotify.com/console/post-playlists/).

the query of the request should contain :

- **q(string)** :Your search query.
- **type(array)** : A comma-separated list of item types to search across
  Allowed values:
  
         "album"
         "artist"
         "playlist"
         "track"
         "show"
         "episode"
         "audiobook"
- **include_external(string)** : If include_external=audio is specified it signals that the client can play externally hosted audio content.
- **limit(int)** : The maximum number of results to return in each item type.
- **market(string)** : An ISO 3166-1 alpha-2 country code. If a country code is specified, only content that is available in that market will be returned.
- **offset(int)** : The index of the first result to return. Use with limit to get the next page of search results.

### A python example
```python

import requests
from prettytable import PrettyTable
table = PrettyTable()
play_list = []

SEARCH_URL = 'https://api.spotify.com/v1/search'
QAUTH_TOKEN = '***********cr0BzLjHFirnYKqT4lq2**********'

class Client():
	def __init__(self,URL, ACCESS_TOKEN):
		self.URL = URL 
		self.ACCESS_TOKEN = ACCESS_TOKEN

	def search_item(self, query, item_type, market):
		#search for a song 
		response = requests.get(
			SEARCH_URL,
			headers= {

				"Authorization" : f"Bearer {self.ACCESS_TOKEN}"
			},
			params={
				"q" : query,
				"type" : item_type,
                "market" : market
			})
		json_resp = response.json()
		return json_resp


client = Client(SEARCH_URL, QAUTH_TOKEN)

type = 'track'
q = 'daruma adios bahamas'
market = 'FR'

result = client.search_item(q, type, market)

table.field_names = ['Song title', "artist"]
nb_result = 5
for i in range(nb_result):
    table.add_row([result['tracks']['items'][i]['name'] , result['tracks']['items'][i]['artists'][0]['name']])
print(table) 	

```

Here I search for *daruma* a song on an album named *adios bahamas* on the French Market.
The result is  :

                                        +-------------+--------+
                                        |  Song title | artist |
                                        +-------------+--------+
                                        |    Daruma   | Népal  |
                                        |    Daruma   | Népal  |
                                        | Trajectoire | Népal  |
                                        |  Crossfader | Népal  |
                                        |   Opening   | Népal  |
                                        +-------------+--------+


References :
 - [Search For item | Spotify for developers](https://developer.spotify.com/console/get-search-item/)
 - [Web API Reference | Spotify for developers](https://developer.spotify.com/documentation/web-api/reference/#/operations/search)

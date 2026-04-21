Код, который должен быть в файле rest_api_demo, но он почему-то не отображается:

import json
import getpass
import requests

title = input('Введите фильм для поиска: ')
api_key = getpass.getpass('Введите ваш OMDb API key: ')

response = requests.get(
    'https://www.omdbapi.com/', 
    params={
        't': title,
        'apikey': api_key
    }
)
response.raise_for_status()

json_data = response.json()
print(json.dumps(json_data, ensure_ascii=False, indent=2))

movie_title = json_data.get('Title')
year = json_data.get('Year')
gengre = json_data.get('Genre')
direcor = json_data.get('Director')
imdb_rating = json_data.get('imdbRating')
actors = json_data.get('Actors')

print(f'Название: {movie_title}')
print(f'Год: {year}')
print(f'Жанр: {gengre}')
print(f'Режиссёр: {direcor}')
print(f'Рейтинг IMDb: {imdb_rating}')
print(f'Актёры: {actors}')

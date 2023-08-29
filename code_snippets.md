```python
import requests
import json

def fetch_all_leagues(url):
    response = requests.get(url)
    data = response.json()
    return data.get("leagues", [])

def save_leagues_to_file(leagues, filename):
    with open(filename, "w") as f:
        for league in leagues:
            f.write(league["strLeague"] + "\n")

def main():
    url = "https://www.thesportsdb.com/api/v1/json/3/all_leagues.php"
    leagues = fetch_all_leagues(url)
    save_leagues_to_file(leagues, "leagues.txt")

if __name__ == "__main__":
    main()
```

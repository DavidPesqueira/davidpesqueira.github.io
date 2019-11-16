
- Python GUI using Tkinter
- NHL Team Stats
- FireBase Login
- and more!

![alt text](https://github.com/DavidPesqueira/DavidPesqueira.github.io/blob/master/App.png)

```
def teamInfo(id): #Team Record

    teamName = entry.get()
    teamId=name_id_map[teamName]
    url = 'https://statsapi.web.nhl.com/api/v1/teams/' + teamId + "?expand=team.stats" #Grabbing from the NHL API
    response = requests.get(url)    
    packages_json = response.json()
    packages_str = json.dumps(packages_json, indent=2, sort_keys=True)

    gamesPlayed=(json.loads(packages_str)['teams'][0]['teamStats'][0]['splits'][0]['stat']['gamesPlayed'])
    teamPoints =(json.loads(packages_str)['teams'][0]['teamStats'][0]['splits'][0]['stat']['pts'])
    wins =(json.loads(packages_str)['teams'][0]['teamStats'][0]['splits'][0]['stat']['wins'])
    losses =(json.loads(packages_str)['teams'][0]['teamStats'][0]['splits'][0]['stat']['losses'])

    label['text']= "Points", teamPoints, "GP", gamesPlayed, "W's", wins, "L's", losses 
```



- Python GUI using Tkinter
- NHL API Access
- Tkinter Firebase Login/Register

![video](https://youtu.be/sLUrJUBy4hY "Initial Code Review")
I started with a weather app using tkinter that I had made a little while back and chose this as an artifact to use that I can enhance by using methods I have learned while enrolled in my Computer Science program at Southern New Hampshire University. Tkinter has great documentation but I did not see any other project that had a Firebase Login system where the database for users would be stored there, instead of hardcoding passwords or storing them in a file. 






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
![alt text](https://github.com/DavidPesqueira.github.io/blob/master/newlogin.png)
![image](newlogin.png)

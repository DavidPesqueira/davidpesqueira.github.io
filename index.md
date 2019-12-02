# Introduction

Throughout my computer science program at SNHU I have taken courses ranging from Calculus to Applied Linear Algebra, Introduction to Information Technology from a business standpoint to reverse software engineering using machine and assembly language in C. I have collaborated with fellow students in a Version Control class using Git, as well as collaborated with other students on coding challenges as Event Coordinator for the ACM SNHU Chapter while I was there. 

On my GitHub page you will see some of the projects of have created such as my personal website, an android application, data structures and algorithms in C++  and more. 

The classes I have done exceptionally well in are ones where teamwork is involved and discussions are encouraged such as Version Control and Data Structures and Algorithms in C++.  

As someone who wants to learn more about security and showcase Python for the powerful language that it is. I chose to do my capstone project in Python.

My final capstone project is displayed below with a link to the GitHub repository. I made a GUI using the python tkinter module. Within this GUI python application I created Software/ Design, incorporated Data Structures and Algorithm (BST) as well as a database (Firebase) to hold user registration. 
***
# Capstone Project

- Python GUI using Tkinter/ Software Design
- NHL API Access / Software Design
- Tkinter Firebase Login/Register / Database
- BST insert and delete Stanely Cup Champions / Data Structures and Algorithms

***

[![codereview](http://img.youtube.com/vi/sLUrJUBy4hY/0.jpg)](http://www.youtube.com/watch?v=sLUrJUBy4hY "Code Review and Plans")


I started with a weather app using tkinter that I had made a little while back and chose this as an artifact to use that I can enhance by using methods I have learned while enrolled in my Computer Science program at Southern New Hampshire University. Tkinter has great documentation but I did not see any other project that had a Firebase Login system where the database for users would be stored there, instead of hardcoding passwords or storing them in a file. 

The project can be found here
(https://github.com/DavidPesqueira/hockeypy)



![image](newlogin.png)
![image](showrecord.png)

This is the design code for the login screen
Using the .geometry feature I can control the window sizes and 
where they open. 

```
canvasLogin = tk.Canvas(top)
canvasLogin.pack()
top.geometry('600x400+650+200')
background_image2=tk.PhotoImage(file='hockey.png')
backround_label2 = tk.Label(top, image=background_image2)
backround_label2.place(relwidth=1, relheight=1)



canvas = tk.Canvas(root)
canvas.pack()
root.geometry('750x350+650+200')

background_image=tk.PhotoImage(file='hockey.png')
backround_label = tk.Label(root, image=background_image)
backround_label.place(relwidth=1, relheight=1)
frame = tk.Frame(root, bg='white', bd=5)
frame.place(relx=0.5, rely=0.1,relwidth=0.75, relheight=0.1, anchor='n')
```


Adding Data Structures and Algorithm

The BST is used to insert and remove as an Easter Egg for those who use the CLI to run the python file

For insterting...


![image](bst1.png)

```
class node(object):
    def __init__(self, data):
        self.data=data
        self.leftchild=None
        self.rightchild=None
        
    def insert(self,data):
        if data<self.data:
            if not self.leftchild:
                self.leftchild=node(data)
            else:
                self.leftchild.insert(data)
        else:
            if not self.rightchild:
                self.rightchild=node(data)
            else:
                self.rightchild.insert(data)
```


And an example...



```
def teamcups():
  
    cups = input("See all teams cup count by typing 'Cups'! or Only the winners by typing 'Winners'!\n")
    if cups == "Cups":            
        bst.insert("Montréal Canadiens      24 Cups Holy COW!") 
```
Also for removing.

![image](bst2.png)


For Firebase login...

```
import pyrebase
from flask import *
import requests
app = Flask(__name__)


config = {
    "apiKey": "YOUR_API_KEY",
    "authDomain": "hockeypy.firebaseapp.com",
    "databaseURL": "https://hockeypy.firebaseio.com",
    "projectId": "hockeypy",
    "storageBucket": "hockeypy.appspot.com",
    "messagingSenderId": "516953468161",
    "appId": "1:516953468161:web:85e81eea16fe8eb774ff00",
    "measurementId": "G-F64QVYNWE5"

}
Firebase = pyrebase.initialize_app(config)
auth = Firebase.auth()
```
![image](register.png)

```
def user_login():
    
    try:
        email =  email_entry.get()
        passwd = passwd_entry.get()
        user = auth.sign_in_with_email_and_password(email, passwd) #To Sign in
        auth.get_account_info(user['idToken'])
           
        top.destroy() 
        root.deiconify()
    except requests.exceptions.HTTPError as e:
        error_json = e.args[1]
        print (error_json)
        error = json.loads(error_json)['error']
        print(error) 

def user_register():
    
    try:
        email =  email_entry.get()
        passwd = passwd_entry.get()
        user = auth.create_user_with_email_and_password(email, passwd) #To Create User
        auth.get_account_info(user['idToken'])
           
        top.destroy() 
        root.deiconify()
    except requests.exceptions.HTTPError as e:
        error_json = e.args[1]
        print (error_json)
        error = json.loads(error_json)['error']
        print(error) 

def exitProgram():
    top.destroy()    
    root.destroy()
    #teamcups.teamcups()
    sys.exit()
```
![image](userdatabase.png)

---
# My Website

[![website](http://img.youtube.com/vi/N4ob0H9b3RM/0.jpg)](http://www.youtube.com/watch?v=N4ob0H9b3RM)

---

# My Mobile App

![image](adroid.JPG)

(https://github.com/DavidPesqueira/CoffeeShop)



# My LED Cube

[![Led Cube](http://img.youtube.com/vi/oVW8duxr60Q/0.jpg)](http://www.youtube.com/watch?v=oVW8duxr60Q "LED Cube")

(https://github.com/DavidPesqueira/LEDCUBE)





# Professional Self-Assessment
Throughout my computer science program at SNHU I have taken courses ranging from Pre-Calculus to Applied Linear Algebra, Introduction to Information Technology from a business standpoint to reverse software engineering using machine and assembly language in C. I have collaborated with fellow students in a Version Control class using Git, as well as collaborated with other students/faculty on events such coding challenges/trivia while I was serving as Event Coordinator for the ACM SNHU Chapter.

I have studied and enjoyed every class I took during my computer science program. None of it was particularly easy, all of it was challenging in a satisfying way. Working with professors, tutors, and fellow students have all helped me get to where I am today when it comes to understanding how operating systems work, creating flow-charts for larger scale software projects, writing pseudo-code and sharing ideas. 

When I began this project, what I had was little knowledge of GUI programming in the Python language. Python itself is a powerful object-oriented language that is growing in popularity for multiple reasons. One reason, being its perceived simplicity. This however isn’t always the case when you are working with some tools that are not documented very well for what you are intending to do. I was able to use problem solving and skills that I gained while attending SHNU to finish the task that I wanted to complete. Within this GUI python application, I created Software/ Design, incorporated Data Structures and Algorithm (BST) as well as a database (Firebase) to hold user registration.
 


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

## Login Screen

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

## The use of Data Structures and the Binary Search Tree Algorithim 
I decided to use a Binary Search Tree to handle my “Easter egg” hidden in the software. When a user exits the program, the output will give the user an option to display all cups one by each team, or only show the winners. 


![image](bst1.png)

***
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
***
***
```
from node import node
class BST(object):
    def __init__(self):
        self.rootnode=None
        
    def insert(self,data):
        if not self.rootnode:
            self.rootnode=node(data)
        else:
            self.rootnode.insert(data)
            
    def getmin(self):
        if self.rootnode:
            return self.rootnode.getmin()
        
    def getmax(self):
        if self.rootnode:
            return self.rootnode.getmax()
        
    def traverseinorder(self):
        if self.rootnode:
            return self.rootnode.traverseinorder()
        
    def remove(self, datatoremove):
        if self.rootnode:
            if self.rootnode==datatoremove:
                tempnode= node(None)
                tempnode.leftchild=self.rootnode
                self.rootnode.remove(datatoremove, tempnode)
            else:
                self.rootnode.remove(datatoremove, None)
```
***

And an example...

***

```
from bst import BST

bst = BST()
def teamcups():
  
    cups = input("See all teams cup count by typing 'Cups'! or Only the winners by typing 'Winners'!\n")
    if cups == "Cups":            
        bst.insert("Montréal Canadiens      24 Cups Holy COW!") 
```

***
Also for removing.

![image](bst2.png)

Using ```__init__.py``` file to import the packages.
```
from hockeyapp import BST
from node import Node
from hockeyapp import teamcups

```

My BST has both the ability to insert and remove data accordingly. This increases the complexity of the code while also gives the user an unexpected function of the program. Something I have always enjoyed in movies, music and games.

The full code is found on my github page for both node and bst. 

## Database/Firebase

Working with Firebase wasn’t the hardest thing about using them to control my user database. It was getting Tkinter to work with it. I knew the code to register in Java, where I have used this before working on an android application, but, that’s almost simpler in my opinion when it comes to GUI programming. Java will sometimes connect the dots for you. Tkinter will not necessarily do that. 
I can delete, and change the user’s password, but I can not view what they have entered, as it is encrypted. 

There are other methods I could use as well in this program such as, when a user registers, they must confirm their email or give them the ability to change their password as well. I felt that for this project that that wouldn’t be necessary. I would recommend this as something to do after all testing is completed on other projects where security might be more of a concern. 


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
# Other Projects
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





# FCC_CS50
Using FreeCodeCamp and Harvard's CS50 lesson on HTML, CSS, Python, and JavaScript

CS50 is a course from Harvard and freeCodeCamp (FCC) to help people get started with coding websites. I am not entirely interested in building websites, but the
course also deals with security and using Python which are why I started it. Now that I have spent a few hours taking the course, I've warmed up a little to the
possibility of me developing websites, as it seems like it could be quite fun, especially when you can do both front and backend development. If you want to
check out the course for yourself, you can find the link [here](https://www.freecodecamp.org/news/learn-web-development-from-harvard-university-cs50/).


(04/10/2023)
Ran into an issue at 6:49:53. Here, we are learning about creating a program that uses SQLite to store flight information. Basically, we have our Django/Python
program that enters our airport information (JFK, New York) into SQLite and so that we can retrieve it. However, when I try to use it to link two airports
together and then save the information, then it gives the following error:

ValueError: save() prohibited to prevent data loss due to unsaved related object 'origin'.

(04/12/2023)
The same issue from a couple of days ago is still persisting. I tried making slight adjustments to the code that might have contributed to the issue and I even tried to delete the SQLite database and migration files, then migrate everything again. That was also unsuccessfull. I will try to fix this issue one more time, otherwise I will move on with the program to keep learning. 

(04/13/2023)
I found the solution!!!
(Found this article)[https://lynxbee.com/solved-django-db-utils-operationalerror-no-such-table/#.ZDgAmfbMIuU] on Lynxbee about how it might be that the database was not initialized properly. To fix the issue:

`\airline>python manage.py makemigrations`

`\airline>python manage.py migrate --run-syncdb`

`\airline>python manage.py migrate`

I found this because I realized that when I tried to save the airports:

`jfk = Airports(code="JFK", city="New York"`

`jfk.save()`

it was giving an error that there wasn't a table to save the information to:

`django.db.utils.OperationalError: no such table`.

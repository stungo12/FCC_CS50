Hello All,


This is a document where I disclose and show how I fixed any errors that I encounter. This was moved from the README file, as I thought having a seperate, troubleshooting document would be a cleaner design than having all my thoughts on one page. It should also be noted that I ran into errors before 04/10, but I didn't think to write down my experience at the time and I don't remember what issues I ran into, so they are left out. If I remember, I might put them in at a later date.

I need to disclose that I worked through this course using a Windows computer. This may be important as commands for Command Prompt (my terminal of choice when using Windows)
might very well be different than if someone was using MacOS or Linux, such as the CS50 instructor using a MacOS. It's also important to know this when you
are searching for information on the web as people may not be using the same operating system as you and so the commands might be different. Just a heads up.


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

`django.db.utils.OperationalError: no such table`

Searching this error on the internet led me to the Lynxbee website. After I put in the above commands and I tried running the program again, it worked and now I can move on to the nex problem :)

(04/13/2023 Sometime later)

Ran into my next problem. At time 6:54:17, we just created a couple HTML files so that we can access our database information from a webbrowser. This however is not working for me and several of my applications are giving me errors, where the imported django libraries and saying that they cannot be resolved at source. So, off to the web I go to search for an answer.

Solved the issue. Was just a simple not putting quotation marks around `flights/layout.html` in the `index.html` file. I am still getting the not resolved errors, but the program now works on a webpage, so I am going to leave the errors (actually I think they are just warnings) for now and possibly look into it later.

Ran into another error, though I think this is one we have dealt with before. I am at time 7:08:19, where we have looked at using the Admin site to change flights and airports, instead of using the command line. Then we created a new class to have passenger information. However, when I try to add a passenger through the Admin portal, it gives me an error about not having a database set up. I think this might be related to the error that flights was giving me and I should just be able to repeat the process. Insert:

`\airline>python manage.py makemigrations`

`\airline>python manage.py migrate --run-syncdb`

`\airline>python manage.py migrate`

And He scores!

Might have been after I put in an extra space between `--run` and `-syncdb`, but we don't need to talk about that. Anyway, it works now, yay!


04/17/2023 - At time (AT) 7:21:51

I am getting what seems to be an attribute error, where Passenger doesn't have an 'objects' attribute:

AttributeError: type object 'Passenger' has no attribute 'ojects'

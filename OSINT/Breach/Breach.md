<h1>SPOILERS AHEAD! PLEASE SPEND TIME TO TRY AND SOLVE THIS BEFORE LOOKING AT THE WRITEUP</h1>


<h2>Difficulty rating : EASY 🟢 </h2> 


<h3>Challenge description</h3>
You managed to pull some interesting files off one of Super Secure Startup's anonymous FTP servers. Via some OSINT work(a torrent or online Password breach site) you have also procured a recent data breach dump. Can you unlock the file and retrieve the key?


<h3>Writeup</h3>

To start the challenge, you need to download a zip file and extract it using the supplied password (hackthebox) containing 3 important documents :
1) A data breach dump containing passwords
2) A job offer letter searching to hire developpers
3) A mysterious Key file

This was the first OSINT challenge I attemped on Hack The Box so I wasn't familiar with this fake company. Because I had no previous information I used what I had available, the 3 files. I started out by opening the juicy public-data-breach.txt file and saw that is used comma seperated values (CSV) so I opened it with LibreOffice Calc (You can use Excel) to have a better understanding of the type of Data I was working with.


** INSERT LIBREOFFICE CALC IMAGE HERE **

In the dump, you can see that there are some names, usernames, passwords, etc. but there is so much information that I don't know what to do with it yet. So I turned my attention to the other 2 files, the Job offer letter and the key. I tried to simply open the key file but it required a password. After quick and cheesy password tests using simple passwords like "admin", "password", "supersecurestartup", "supersecurepassword", I found out that it would take an eternity to try and guess it and the info must be hidden somewhere in the data breach dump. 

I then pivoted to the last remaining document, the job offer letter which had no usefull information in the letter itself except the domain name of the company @supersecurestartup.com BUT I thought to myself, this is an OSINT challenge, why not look at the documents properties. There I found ou first usefull hint! The document was created by **Bianka Phelps** on **2019-03-26**. HEY, A NAME! 

** INSERT PROPERTIES IMAGE **

I quickly went to cross reference this name in the previous data breach dump file and low and behold, Bianka Phelps was in it with the password "Love!July2018"
So I tested this directly in the Key file but to no avail, it didn't work. I looked at the password again and realised that there was a month and a year inside it, maybe this company has a password rotation policy that forces employees to change their password every so often and Bianka chose to have a pattern based on time in her password. Using this knowledge + the hypothesis that the key was created the same day as the job offer letter, I tried "Love!March2019" and POOF, IT WORKED!

** INSERT PASSWORD IMAGE **

Out came a key that seemed to be base64 encoded so I ran to my trusting conversion website (https://gchq.github.io/CyberChef/) and converted it into plain text from base64 and out came the real key which I submitted to HTB succesfully!

(I won't post the key here, please try the challenge yourself, it's good practice)

<h3>Takeaway</h3>
1) Always use passwords that don't contain recuring patterns if you have to change it. An old breach can come back to haunt you!


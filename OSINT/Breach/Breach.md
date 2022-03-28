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

I then pivoted to the last remaining document, the job offer letter which had no usefull information in the letter itself BUT I thought to myself, this is an OSINT challenge, why not look at the documents properties. There I found ou first usefull hint! The document was created by Bianka Phelps on 

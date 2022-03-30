<h1>SPOILERS AHEAD! PLEASE SPEND TIME TO TRY AND SOLVE THIS BEFORE LOOKING AT THE WRITEUP</h1>


<h2>Difficulty rating : MEDIUM 🟡 </h2> 


<h3>Challenge description</h3>
Super Secure Startup's private information is being leaked; can you find out how?


<h3>Writeup</h3>

Now before we begin, i'd like to state that this is an easy challenge but I stumbled so much on one part of it that I categorized it as medium

So first off, like always let's see what we have to work with? We have a zip file containing a password protected "Username" and "Password" zip files. We also have a small description indicating the name of the company "SuperSecureStartup" and you know that there is a breach somewhere.

I started by checking all of the files for general properties and tried entering popular weak passwords to no avail (EX: Admin, Username, Password, etc.)

I was a bit stumped here since we didn't have a lot to work with, so I decided to google the company name and here the work begins. I found a Twitter account linked to SuperSecureStartup containing multiple differrent posts. 

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/SuperSecureStartup_TwitterAccount.png">

I started searching through these posts and found multiple accounts linked to it : 
- Bianka Phelps
- Johanna Boyce
- Alia Mccarty
- Josh Terranwald

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/Bianka_Phelps_Discovery.png">
<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/Johanna_Boyce_Username_Discovery.png">
<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/New_Employee_Twitter.png">

These twitter accounts offered us a treasure trove of information and the first major find I got was on Bianka Phelps account when she posted an image of the engineering whiteboard. 

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/Password_Discovery.png">

For the ones with 20/20 eyesight, you might have noticed in the bottom left a cleartext password that seems to be pointing to an SSH login. If we look at the files we recieved, the base file hints to an SSH login with the filename being "mock_ssh_login".

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/Cleartext_Password.png">

So I tried entering the password we found "SupSecStart#Winter2018!" but it wasn't correct, I then recognized the password pattern which indicates a specific season for a specific year and tested it with the date at which the post was made (25th March 2019) "SupSecStart#Spring2019!" and it didn't work either! 

Here is where I fumbled around for quite a bit, I knew that the username file and password file probably had different passwords and I started expecting a username as the password for the username file and a more complex password for the password file. I started by trying SSH style login information with the different twitter handles of the employees I found (EX: JTerranwald@supersecurestartup.com), I tried with simply the twitter handles, the fulle names and nothing seemed to work. 

I tried looking at other posts from the twitter accounts, nothing....
I tried looking at different social media (Found a facebook), nothing....
Retested the cleartext password we found by rewriting it multiple diffrent ways, nothing....

After about half an hour of snooping around I wen't back to read the twitter posts more in details and there I found the twitter post that saved the challenge! 
A post done by Johanna Boyce and one that I had already showed you above!! I had completely glossed over this detail but Johanna mentions j.boyce@supersecurestartup.com as her email address! 

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/Johanna_Boyce_Username_Discovery.png">

This indicated that the naming convention for usernames in the company might be first letter of the first name, dot, family name! I tested Josh's account first since he's a new hire and a developper so he must have a use for an SSH login and BOOM! Worked, unlocking the password zip to be extracted and I retested the cleartext password I found, "SupSecStart#Spring2019!", and bim bam boom, there was the final flag!!



(I won't post the key here, please try the challenge yourself, it's good practice)

<h3>Takeaway</h3>
1) Posting on social media can lead to leaking private company information even if the intention is good. Be mindful of what you post 


<h3>Mind map</h3>
<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/Mind%20Map%20.png">

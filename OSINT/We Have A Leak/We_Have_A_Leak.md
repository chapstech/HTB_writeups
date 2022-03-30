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

For the ones with 20/20 eyesight, you might have noticed in the bottom left a cleartext password that seems to be pointing to an SSH login. 

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/Cleartext_Password.png">




(I won't post the key here, please try the challenge yourself, it's good practice)

<h3>Takeaway</h3>
1) Posting on social media can lead to leaking private company information even if the intention is good. Be mindful of what you post 


<h3>Mind map</h3>
<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/OSINT/We%20Have%20A%20Leak/Images/Mind%20Map%20.png">

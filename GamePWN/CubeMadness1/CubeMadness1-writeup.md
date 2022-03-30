<h1>SPOILERS AHEAD! PLEASE SPEND TIME TO TRY AND SOLVE THIS BEFORE LOOKING AT THE WRITEUP</h1>


<h2>Difficulty rating : EASY 🟢 </h2> 

<h3>Challenge description</h3>
Gotta collect them all.

I'll preface this by saying that this is the first GamePwn I try but I had a bit of experience around 15 years ago with one of the tools we are going to use, which is Cheatengine.

I started by trying to play the game and understand the basic rules. It seems to be quite simple, move with the WASD keys, Jump with space and collect 20 cubes. However, there are only 6 cubes in the scene!

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/GamePWN/CubeMadness1/Images/game.png">

The challenge is pretty straight forward but you need to know which tools to use. I am a Unity engine hobbyist so when I recieved the original file I was glad to see that the game was made in Unity Engine.
My first step was to naturally try to open it with Unity or to import ressources and asset files into unity to see what I can extract. Spoiler, it didn't work! At least for me :)

So I pivoted to an old tool I remember using in my teens when I was messing around with trying to hack into games, Cheat Engine! This was a super tool that allowed you to read the memory contents of a program while it was executed wich was a fast and easy way to cheat in single player games and even some multiplayer games.

With nothing to lose in a VM, I installed this sketchy tool. (For windows users, you might need to allow the program through your antivirus, do at your own risk)

Lets power it up!!

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/GamePWN/CubeMadness1/Images/cheatengineopening.png">

AHHH the nostalgia! 

The way the tool works (Or the way I used it in the past) is that you can input a value you are looking for in memory and modify the corresponding address's value. However you will soon see that there are thousands of indentical values in memory, we will ahve to refine our search.
Let's deal with that later, with cheatengine open, lets run the game! 
Now to tell cheatengine what program you are searching through, you will need to select it in the pane you see below while it is running.

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/GamePWN/CubeMadness1/Images/open%20process.png">


Now the work starts, we know that the objectif of the game is to get 20 cubes, so lets try to hack our score to show 20/20.

In cheat engine, i'll precicely target this value starting with a value of 0 in the value field and click "New Scan"

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/GamePWN/CubeMadness1/Images/new%20scan%200.png">

Out comes a tooon of results! Way too much to handle so lets refine our search with a second search. In the game I will jump to try and get my first cube. Now with a score of 1, i'll input this new value in cheatengine and do a second scan. Cheat engine will track the adresses that follow this pattern

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/GamePWN/CubeMadness1/Images/1%20cube%20collected.png">
<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/GamePWN/CubeMadness1/Images/next%20scan%201.png">

Still a lot of addresses, 40 080 to be exact!! So I'll grab a second cube and same this, input this value in cheat engine and make another scan. Continue this process until you have a reasonable amount of addresses. Here, it took me 4 cubes to get 3 addresses which is a more manageable number.

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/GamePWN/CubeMadness1/Images/adresses%20found%204.png">

Once we have a reasonable amount of addresses, you can double click on each one to bring them to the pane underneath and if you double click on the value field, in our case we don't wan't 4 cubes collected, we wan't 20 so we just have to modify the 4 for 20. Do this for each address or until you see the number of cubes collected change!

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/GamePWN/CubeMadness1/Images/modifying%20values.png">

TA DAM!

<img src="https://github.com/olivierchaput/HTB_writeups/blob/main/GamePWN/CubeMadness1/Images/win.png">



(I won't post the key here, please try the challenge yourself, it's good practice)

Takeaway
- Allowing clients to modify core values to the game is a bad idea if you wan't to prevent cheating. Memory can easily be accessed and modified at will pretty easily. For a multiplayer game, a client-server model with server side logic/validation would be more appropriate mixed with a good anti cheat software. 


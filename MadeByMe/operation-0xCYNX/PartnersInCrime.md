**Challenge name: Partners In Crime
Category: OSINT
Difficulty: Medium **

**Description**:
You know all about 3ch0.
You are aware of the attach on CYNX.
What we don’t know is who was standing beside him.
Amongst those recovered pieces of evidence, one person repeatedly reappears. This person is someone close enough to be trusted, but careful enough not to give their name. Yet still human enough to forget something.
A secret love note, written but never sent, and never deleted, becomes the only clue we now possess.
You need to find the following:
•	The real identity of the individual connected to 3ch0
•	The recipient of this message
•	The operation name that ties them together

**Flag format:**
CYNX{the_person_name_the_girlfriend_name_the_operation_name}

**Paid Hint: Braille.**
-------------------------------
<img width="825" height="464" alt="image" src="https://github.com/user-attachments/assets/30194de9-a329-4d13-8e76-f69ff19d02c8" />

Players will start with the message above presented to them, it has some sort of love message that we don’t really care for.
Now if you look closely, you will see some filled circles, below is an illustration for clarifying the concept:

<img width="748" height="418" alt="image" src="https://github.com/user-attachments/assets/562de1b7-6218-474d-ad3d-71af39cb1cf9" />

It’s funny how most of you were blind, yet you still couldn’t read even in Braille XD. 
Now for those who are not familiar with what this is, it is Braille writing system, it allows blind and visually impaired people to read with their fingertips where the pattern in real life is a collection of raised dots on a page.
And no it was not impossible to see it, at least 3 teams in operation 0xCYNX managed to read it correctly!

<img width="516" height="462" alt="image" src="https://github.com/user-attachments/assets/66a103b6-4e07-4eba-81e1-3222cdf8fb76" />

Once you get a hold of the translation “lu5wim5” all you got to do is basic OSINT 101, look up the text online, you’ll find out that it is a username for an X account.

<img width="506" height="623" alt="image" src="https://github.com/user-attachments/assets/1661578b-b351-4cd0-a809-7375f47bc6e3" />

All the posts on that account don’t really matter, except one:

<img width="603" height="545" alt="image" src="https://github.com/user-attachments/assets/9ab36229-7384-4dcb-9f79-99e799e485af" />

For those paying attention to the tweet you will notice two things, the first is that the Caption talks about some Video that got posted, the second thing is that the Image has a drawing of a map, along with the coordinations next to it:

<img width="923" height="519" alt="image" src="https://github.com/user-attachments/assets/7de4a63e-88bc-43b5-95fc-f7affbbde905" />

28.85236, -17.90350  (it is a place called “Punta de la Manga” in one of the Canary Islands, which belong to Spain.)

<img width="759" height="557" alt="image" src="https://github.com/user-attachments/assets/1a4bffbe-5746-4854-8349-1b66999d4a77" />

Now the second part of the post has been solved, which is finding the location, So back to the first part that talked about a video being posted, where else would people post videos other than youtube.

After a little bit of googling, you will find out that there is one online tool that helps you find youtube videos via location:
https://mattw.io/youtube-geofind/location

<img width="452" height="427" alt="image" src="https://github.com/user-attachments/assets/36c92af4-b7ad-40e9-80c6-3dfe3b5c4710" />

Drag the pin to the same exact location, reduce the radius to 1 km to be more specific, hit submit, and You will find a video posted exactly there!

<img width="975" height="767" alt="image" src="https://github.com/user-attachments/assets/80108cf1-9391-4098-821e-0332bffb6cc3" />

We got the first requirement, his name! 
**“Luis Porfavorianto”**

Now if we check the description of that video we will find this:

<img width="975" height="123" alt="image" src="https://github.com/user-attachments/assets/40c38cf0-b1cc-43c5-a06e-5a70f3bd0039" />

With this link for the other video: https://www.youtube.com/watch?v=CjSSFmzKK2s
If you try and open it, You will find out that the video has been removed: 

<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/7d3ae87d-e703-4c0a-824d-b644de6cb58b" />

Now your only chance of finding the video is through tools that archive youtube videos, there are many different websites that do that, but https://findyoutubevideo.thetechrobo.ca/
Is the best, where it searches for the video in all the archiving websites all at once.
Result:

<img width="783" height="324" alt="image" src="https://github.com/user-attachments/assets/279e8b9b-55db-4441-9373-4a65f671ec0e" />

Click on one of them, and you’ll find a useless video about his take on the top 3 animes (goated btw)
But there is important information in the description of this deleted video as well!

<img width="975" height="1158" alt="image" src="https://github.com/user-attachments/assets/7f0b164b-f884-453e-8a67-dad503dd22e4" />

@favoorindahouse
Yup, you guessed it! It’s another X account.
Finally, if you go through the secret X account , you’ll find everything else you need to solve the CTF Challenge!

<img width="911" height="231" alt="image" src="https://github.com/user-attachments/assets/3915b2ed-bb78-4d2a-8d4a-f9b10d9ef69a" />
<img width="911" height="260" alt="image" src="https://github.com/user-attachments/assets/f2b2d9cf-6c5e-48c3-b275-e51cd559af80" />

**Final Flag: 
CYNX{Luis_Porfavorianto_Sarah_Smith_The_Giant_Crime}**

And now for the one hard question in the first phase:
Description: “I received an image from my friend Wala, the math genius ***= I used to play Chapteh with. It holds secrets beyond what the eyes can see or the ears can hear. Can you help me retrieve the hiDDen message?”

 The Challenge came with a “Chapteh.jpg”, and a zip file “I_MISSED_MY_PASSWORD.zip”

 , this one took a while to solve, as I never had experience with the tool I used here before, so I had to figure out the flags with the help of my friend GPT.

 For starters, no hint within the properties/files details, the hints that can be retrieved from the description are: “the math genius”, “beyond the eye can see or the ear can hear”, “hidden message”

 So I opened the hex of the file, and noticed too things, first is that the hex was lengthier than usual, and it had a weird format of data:
 ![image](https://github.com/user-attachments/assets/0f42e503-25e4-4d3f-95e2-76759f65f9f9)

“LAME3.100” turned out to be an encoding of an audio.
Next thing is to find a way to be able to extract that audio:
![image](https://github.com/user-attachments/assets/adad5f2b-9378-4668-8157-66b603a06383)
![image](https://github.com/user-attachments/assets/22d8bc32-8312-4b59-843f-742c281613c9)

First I tried it without the extra flags.
“dd if=Chapteh.jpg of=Chapteh_trimmed.mp3”
And got a missed up mp3 file that had nothing.
So I kept looking into the hex to see if I can figure out where the skip value is at.

This is what any jpg trailer (where the jpg hex ends) looks like :
FF D9
So I searched in the hexedit to know at what hex I can start skipping
![image](https://github.com/user-attachments/assets/fcbebd7c-a6a9-4eb9-a2ea-5886ab7ab31c)

When I saw the dump I knew I was on the right track, as I saw “major_brand.mp4”, and “ID3”  which is a tag related to audio hex.

0002C560 in hex is the line it was on. The skip flag’s value takes decimal only, so when converted it is 181600
![image](https://github.com/user-attachments/assets/05e3a01e-2015-4f89-8089-f328cffac190)

bs: Block size (size of each read/write operation).
skip: Number of bytes to skip from the start of the input file.

Then I opened the hexedit again to remove half of the first line of hex as it still belongs to the image:

![image](https://github.com/user-attachments/assets/a3e7d77c-7ceb-490a-aa1d-d1a29c2d4f09)

after saving the file again. I listened to it and there was an audio that sounded like those old phones when you click on the numbers to dial
so…
![image](https://github.com/user-attachments/assets/75ac2ea1-db2d-4d10-b334-4c4353fe1b65)

![image](https://github.com/user-attachments/assets/b728e246-d368-4142-8455-4f15e88574a2)

"899999*222174433777*22200555"

Here is where it gets annoying:
From how some of the numbers are repeated, I thought that the numbers might have something to do with the telephone keypad 

![image](https://github.com/user-attachments/assets/88df6d3a-7af8-470b-a4c2-f1b180bdf617)

; using dcode

![image](https://github.com/user-attachments/assets/b14b0bd3-2b90-431c-ab78-cba426ba7023)

The output made no sense, so I tried doing it manually:

![image](https://github.com/user-attachments/assets/e4bd015e-9682-4b6c-b503-701324bfbe74)

And made corrections on my own, such as that five 9’s presumably means that the fifth click on the number 9 will be encoded as “9” instead of “ZW”,
And then, there was a space, if you replace it with Its corresponding number, the text starts to make sense, as it says “T9_C1PHER…”
Note: T9 cipher is something related to this decoding I was doing:

![image](https://github.com/user-attachments/assets/f5f38e86-a4a8-49c9-879c-923ed2555ff6)

Not to bother you any further… this whole decoding was all wrong, and it didn’t work as the passcode for the zip file  -_-
If you go back to the hints in the description, it says “a math genius”,
So I tried something more simpler, Multiplying the numbers beside the stars “*”, AKA multiplication sign.
899999*222174433777*22200555
= 4,439,151,230,598,394,951,353,765
4439151230598394951353765
and it turned out to be the correct password

 ![image](https://github.com/user-attachments/assets/8c9beb06-1e82-409c-879a-1de3a38f0f68)

Finally, here is the flag:
“BAT{F33t_0nly_N0_H4nds_Ch4pt3h}”

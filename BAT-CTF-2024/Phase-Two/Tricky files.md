The description: "I attempted password cracking but was unsuccessful. Your task is to retrieve the password for the file and explore it!!"
the challenge came with a rar zip file that had protection.

unfortunately, we only managed to solve half this question in the competition, then finished it after the competition ended, as the time was very limited.
ok so to start, we use the unrar command to unzip the file
![image](https://github.com/user-attachments/assets/33cc5c0a-4e7e-4b88-b2a1-b999325420c3)

but the file requires a password, so, we tried using john the ripper.

first we exrtact the hash of the file into a new file using :
"rar2john FLAGS.rar > hash.txt"

then, we use john the ripper with the rockyou famous wordlist using the following command:

![image](https://github.com/user-attachments/assets/50defa37-abbd-4f5d-91c1-7fb6e8cf17d2)

now that we have the password "pookie", we go again and extract the data.

![image](https://github.com/user-attachments/assets/3315ba21-292c-4c2c-a3ee-b671f772ebe8)

to be on the safe side, i never replaced the file, i just renamed every extracted file with a different name to make sure to view all the data regardless.

![image](https://github.com/user-attachments/assets/fe41e3ad-774c-4031-86e2-e8a9d9b13da2)

file1 contained: "aXQncyBub3QgaG93IGl0IGxvb2tzLg==" which is the base64 of "it's not how it looks."
file3 contained: "eW91J3JlIGNsb3NlISE=" which is the base 64 of "you're close!!"
fiel2 contained: "aXQncyBob3cgaXQgbG9va3Mu" which is the base64 of "it's how it looks."
as well as: "XHg0OFx4MzBceDcwXHg3M1x4NjNceDMwXHg3NFx4NjNceDY4XHg1Zlx4MzFceDczXHg1Zlx4NzRceDMzXHg2ZVx4NjdceDc0XHgzM1x4NmVceDY3XHg1Zlx4MzFceDczXHg1Zlx4NzRceDMxXHg2ZVx4NjdceDc0XHgzMVx4NmVceDY3DQo="
this is the flag, first we decrypt it with base64 decryption, then we get a hex value as shown:
![image](https://github.com/user-attachments/assets/f7b46391-618e-407c-a1bd-d75ebcdfb1a1)

\x48\x30\x70\x73\x63\x30\x74\x63\x68\x5f\x31\x73\x5f\x74\x33\x6e\x67\x74\x33\x6e\x67\x5f\x31\x73\x5f\x74\x31\x6e\x67\x74\x31\x6e\x67

this value is again when decrypted, becomes the flag:

![image](https://github.com/user-attachments/assets/c891c31d-f66a-4140-a522-2df00a352bbd)

finally the flag is: "BAT{H0psc0tch_1s_t3ngt3ng_1s_t1ngt1ng}"

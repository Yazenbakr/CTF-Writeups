![image1](https://github.com/user-attachments/assets/92751858-1847-40af-b838-348b65015269)Description: “Ive hidden a confidential secret inside an image, but unfortunately, I forgot the password for my old Chapteh picture. Can you help me find the secret?”
This challenge came with one image “chapteh.jpg”

The first thing I did since I didn’t have the password was testing trying to extract the data using binwalk, but that lead to no outcome:

![image](https://github.com/user-attachments/assets/376bc9ae-e4b6-42f9-97e5-0f1f2c7e8d85)

Then I tested with steghide, leaving the passphrase empty, that didn’t work at well:

![image](https://github.com/user-attachments/assets/67d6c64e-7f7b-4628-84b3-939d921917c0)

Next step was to look for any hints that might help find the passphrase, if you go through the file using the “File”, or “Exiftool” command, you can find the comment "S0_m4ny_c0l0rs"

![image](https://github.com/user-attachments/assets/6f6e57f7-54fb-444f-aab2-1b85ca7f504b)

I used this as the passphrase for steghide, and the Maze zip got extracted
The Maze.zip contained a “Click_here” File, using the tree command, as the name of the challenge suggests, we see these numbered files that look like an encrypted text of some kind,

![image](https://github.com/user-attachments/assets/09a11cd7-96fe-4325-aa2f-7ffde75b75e9)

Finally, here is the flag:
![image](https://github.com/user-attachments/assets/91089497-982d-4549-8773-6c62fa9e5769)

“BAT{F0cus_F33t_N_C0ntrol_Ch4pt3h}”

Description: "my friend Rijndael send me this old photo of me playing teng-teng, i believe it's more than a photo, help me to find it out!!"

this challenge contains only an image "teng-teng.png"

to solve this Challenge
first if we exiftool the image we can find a comment that has a decrypted text of some kind.
![image](https://github.com/user-attachments/assets/69f54d23-1bd7-49cb-9ae4-429a06cc0602)

fe685a7aa83947125bd66e643d1b695ccee76f40f8534e30a7ee8fdeed5a928f380ab3a0ef7466c162c8ae4fdc2c79f6

this was the first thing I found, then, i extract the hidden data using binwalk through the following command:
**sudo binwalk -e teng-teng.png --run-as=root**
![image](https://github.com/user-attachments/assets/1304d9fd-6a06-4ad3-be09-d0969f00418c)

![image](https://github.com/user-attachments/assets/402e84be-f8ab-4b0d-833e-e76118538575)

the extracted file has many directories within it, to view everything clearly i used the tree command.

![image](https://github.com/user-attachments/assets/e04cf155-722c-4698-82a7-24df1684909e)

so i cat into the My notes.txt to see what it contains 
![image](https://github.com/user-attachments/assets/cf6891e3-5c0f-4ef2-9b34-b9c256260b85)

but if you scroll upwards enough you will find hidden information

![image](https://github.com/user-attachments/assets/00337443-850f-439b-85ac-cbdc31ceb8b0)

![image](https://github.com/user-attachments/assets/a49d6c21-53ec-4af5-9d3e-f3347976c833)

![image](https://github.com/user-attachments/assets/deb6329d-c561-4450-b92c-ee829d3b1081)

Key: b2a3e6f45d7c9d8a2e4f7c1b5d9e4f3a7b8c9d0e1f2a3b4c5d6e7f8a9b0c1d2e
IV : 1a2b3c4d5e6f7a8b9c0d1e2f3a4b5c6d

so obviously, AES Cipher is used.
 now i have all the IV, the Key values,and the encrypted text to decrypt.
![image](https://github.com/user-attachments/assets/f80a62ed-e5c4-4238-b75c-bf80c9fd7547)

finally here is the flag:
"BAT{t3ng_t3ng_1s_pl4yground_g4m3}"


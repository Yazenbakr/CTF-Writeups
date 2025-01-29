**challenge name**: getting through it all
**Category**: Web Exploitation
**difficulty**: easy to medium
**Description**: 
Do you need to go through it all to find the flag, or is the flag what gets you through it all? 

Follow the numbers, and don’t forget that what you seek might already be in your hands.

**Hints**: 
1.	Hint 1 (Low cost): “Start with the basics—look closely at the URL. Sometimes, a simple key value can change everything.”
2.	Hint 2 (Medium cost): “Every number you enter takes you one step closer, but only one holds the key to the next.”
3.	Hint 3 (High cost): “The final piece is a cookie, will becoming the admin give you permission to certain pages.?”

-----------------------------------------------------------
the challenge starts with this page:
![image](https://github.com/user-attachments/assets/29f450a1-96b2-4b0e-869b-1bd5d5746be0)
The message reads: "Can you find the flag? :)"
There’s nothing particularly special here—no hints in the source code, and no cookies are available to view.

To progress, the player needs to exploit Insecure Direct Object Reference (IDOR). This can be done by guessing URL parameters (e.g., admin=1, flag=true, etc.).
The correct parameter is www.example.com?flag=0, which redirects the player to another page with a different message: 
![image](https://github.com/user-attachments/assets/93822754-42b9-4ee5-b808-ee1aca223064)

As the player increments the flag parameter (from flag=0 to flag=11), they encounter different messages. However, two pages stand out with special messages:
on **www.example.com?flag=2**, it says this:
![image](https://github.com/user-attachments/assets/d8ce2d0b-f39c-4dc9-9503-312329bfcaf2)
To most players, this might appear as a server-side error, but it clearly states: "You do not have permission to access this page."

and on **www.example.com?flag=11** the message will say: 
![image](https://github.com/user-attachments/assets/43daff37-7bf0-4b02-8e61-0cb8cb1f787c)
as I mentioned before, Up until this point, no cookies were available to view on any of the pages. However, upon reaching this page, a new cookie is set:
![image](https://github.com/user-attachments/assets/75f1669f-70db-4c8b-b35c-f8feb2139b6f)

the cookie value is an encrypted base64 text"c3RpbGwgaHVuZ3J5PyBZV1J0YVc0NmVXVnpYMmx1WkdWbFpB", so we decrypt once:
![image](https://github.com/user-attachments/assets/a3fbd2d6-90f7-4e9d-b201-da922a350e1f)

and decrypt again "YWRtaW46eWVzX2luZGVlZA":
![image](https://github.com/user-attachments/assets/8b68bde4-0727-429d-8c60-b8b8d953957b)

output is : "admin:yes_indeed", This output is itself a cookie (key:value pair).

manipulating the cookie would allow session fixation, so we try and replace the cookie:
![image](https://github.com/user-attachments/assets/8fb13f5b-c826-46ec-887b-26cab78fe27a)

once that is done, if we go back to **www.example.com?flag=2** this time the page will open as we have "Permission", and the flag can be found:
![image](https://github.com/user-attachments/assets/bb207872-a377-45f6-afda-e4bc4a604f70)

-----------------------------------------------------------
**Exploited Vulnerabilities**:
Insecure Direct Object Reference (IDOR): Guessing URL parameters to access restricted pages.

Information Disclosure: Progressive hints and messages guiding the player.

Cookie Manipulation: Decrypting and modifying cookies to escalate privileges.

Session Fixation: Using a manipulated cookie to gain unauthorized access.

Base64 Encoding/Decoding: Decrypting encoded data to reveal sensitive information.


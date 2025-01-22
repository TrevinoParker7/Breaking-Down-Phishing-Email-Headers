#  Email Analysis (Phishing)

---

### 🚀 **Breaking Down Email Headers: A Simple Guide** ✉️✨  

Let’s start at the top! 

---

![Screenshot 2025-01-21 174720](https://github.com/user-attachments/assets/59148871-6607-4f9b-ad6c-fbaf4f74f362)

---

#### 📩 **Delivered To**  
This field shows who received the email. In our example, it’s **themajoronar@gmail.com**.  

---

![Screenshot 2025-01-21 175710](https://github.com/user-attachments/assets/fa7f8aa2-d9b2-4d63-a29b-37f3cdccf6e9)

---
#### 📨 **Received By**  
This section lists email servers that handled the email, similar to how 📦 mail moves through several post offices.  
- 🥇 The **first "Received By" field at the top** refers to the mail server closest to the recipient.  
- 🥈 The **first "Received" field at the bottom** is closest to the sender.
---

![Screenshot 2025-01-21 180347](https://github.com/user-attachments/assets/a564de9c-5ea3-496e-9de6-964c6a1f3886)

---

![Screenshot 2025-01-21 180609](https://github.com/user-attachments/assets/374dc0d5-ea68-4780-883a-ff83a6ee66a4)

---

#### ❌ **X-Headers**  
Headers with an **X** prefix are optional. They're added by tools or servers to provide additional information.  

---

![Screenshot 2025-01-21 180916](https://github.com/user-attachments/assets/5f1582f2-6228-42ba-9ae8-1fd0047925eb)

---

#### 🔗 **ARC Headers (Authenticated Received Chain)**  
These are used for email verification. They let a trusted intermediary server digitally sign the headers for authentication.  

---

![Screenshot 2025-01-21 181146](https://github.com/user-attachments/assets/3469a1e7-a0df-4cc7-bf83-1f8a76f2dccf)

---

#### 🔄 **Return-Path**  
This is the address used if the email fails to send. If you’ve ever received a "failed delivery" email, this address is likely in the **Return-Path**.  

---

![Screenshot 2025-01-21 181303](https://github.com/user-attachments/assets/96bef85e-a8a0-45cd-af01-3f2bd74f0d1f)

---

#### 🛡️ **Authentication Results**  
Here’s where email protection statuses appear:  
- **SPF**: It failed, meaning the sender's domain, **microapple.com**, doesn’t recognize the mail server **9399.104210**.  
- Failing SPF is a 🚩 **red flag**—a good reason to dig deeper!
  
---

![Screenshot 2025-01-21 181649](https://github.com/user-attachments/assets/a1b7c795-d8cf-47d8-b130-acecf51b04f5)

#### 📬 **Recipient and Sender Info**  
- **To**: The recipient (themajoronar@gmail.com).  
- **From**: The sender (**microapple.com**).  
- **Reply-To**: This address is used when replying. In this example, it’s suspicious because the **From** domain and **Reply-To** domain don’t match!

#### 🎨 **Content Type**  
This tells the mail server how to render the email. For instance:  
- **Multi-part/mixed**: Indicates multiple formats in the email.  
- **Boundary**: Marks where content starts and stops.  

#### 🆔 **Message ID**  
A unique identifier for the email, helping track its journey.  

#### 🕒 **Date**  
When the recipient received the email (but keep in mind, this field can be spoofed!).  

---

### **Email Discrepancies Detected 🚩**
- **Reply-to Address**: 📨 This is the email address that the recipient uses when they hit "Reply." Here, it’s set to a **pastor.com** domain.  
- **From Address**: The email claims to be from **micro.apple.com**.  
- 🚩 *Suspicious Alert*: When the "From" and "Reply-to" addresses don’t match, it’s a potential red flag.

![Screenshot 2025-01-21 182341](https://github.com/user-attachments/assets/d9cc3040-15c4-4b95-aaab-2e6b3b1cb6a4)

---

![Screenshot 2025-01-21 182631](https://github.com/user-attachments/assets/43acb80a-9b3f-4354-9434-bc11205398bb)

---

### **Analyzing the Content Type 📝**
- The **Content-Type** field indicates how the email content should be displayed.  
- Here, it's set as **multipart/mixed**, meaning there are multiple formats (like text and attachments).  
- It also uses a **boundary**, marking where each section of the content starts and stops.
  
![Screenshot 2025-01-21 184633](https://github.com/user-attachments/assets/caa5bb05-6861-4693-95c5-d1271e625151)

---

### **Unique Identifiers and Spoofing Tricks 🔍**  
- **Message ID**: A unique identifier for the email.  
- **Date Field**: 🕒 This can easily be spoofed, so don’t trust it blindly.
---
![Screenshot 2025-01-21 185332](https://github.com/user-attachments/assets/4b1dba79-2ce5-4ebd-bdc6-c18e1f8ef024)

---

### **Digging into Email Content: The Mystery Begins 🕵️‍♂️**  
1. **Boundary Encountered**:  
   - First, the **plain text content** is rendered.  
   - Encoding: **Base64**.  
   - Decoding it via **CyberChef**, the message revealed:  
     > “Hi Major! The abducted Candians are safe. Send 1 billion candies with a spaceship. Solve the attached puzzle for the next step!” 🚀🍬  

---
![Screenshot 2025-01-21 185520](https://github.com/user-attachments/assets/d8f18ddf-d7dc-48a0-bd33-5ed124f57c13)

---

2. **Attachment Analysis**:  
   - Content-Type: `application/pdf`.  
   - Encoding: Base64.  

---

### **Attachment Decoding 🚨**  
- Using **CyberChef**, the attachment decoded into a **zip file** instead of a PDF.  
- File signature check 🔑 revealed it was **not** a PDF but a ZIP archive.  

---

### **Extracting Files from the ZIP 📂**  
- **Files Found**:  
  - **daughter’s_crown.jpg**  
  - **money.xlsx**  

---

### **File Type Verification 🧩**  
- **daughter’s_crown.jpg**: Verified via file signature as a JPEG image.  
- **money.xlsx**: Verified as a valid Excel file.  

---

### **Hidden Clues in the Excel File 🔐**  
1. Opened using a file viewer (like **Square X**) to inspect contents.  
2. Suspicious: Sheet 3 appeared blank.  
3. Cleared formatting to reveal hidden Base64 text:  
   > “The Martian Colony 🛸”  


### 🔍 **Decoding Base64 Content**  

#### Step 1: Copy the Content  
Highlight the Base64 content, right-click, and copy it.  

#### Step 2: Use CyberChef 🛠️  
1. Paste the content into **CyberChef**.  
2. Drag the **"From Base64"** operation to the recipe area.  
3. Voilà! You’ll see the decoded output below.  

For example, the decoded message might say:  
> **"Hi Major! The abducted Candians are safe. Solve the puzzle I sent for the next step."**  

#### Step 3: Save the Decoded Content  
Click **Save Output**, name it something like **email.txt**, and save it.  

---

### 📎 **Handling Attachments**  

Attachments also use Base64 encoding. Let’s decode them step by step:  
1. Locate the **boundary** for the attachment.  
2. Copy the Base64 content of the attachment.  
3. Decode it in CyberChef.  

#### 🧑‍💻 **File Signatures: Verifying File Types**  
File names can be misleading. Always check the **file signature**:  
- Copy the first few bytes of the file (e.g., **50 4B 03 04**).  
- Use tools like **Gary Kessler's File Signature Database** to verify the file type.  

For instance:  
- If it’s a ZIP file but named **.pdf**, you know something’s off!  

---

### 🔓 **Extracting Files Safely**  

Always use a **virtual machine** for analysis to avoid infecting your host system. Once extracted, verify each file:  
1. Open the file in a hex editor (like **HxD**).  
2. Check the file signature against its extension.  

For example:  
- **Daughter's Crown**: Signature **FF D8 FF E0** → It’s a JPEG file.  
- **Good Job Major**: Signature **25 50 44 46** → It’s a PDF file.  

---

🌟 **Pro Tip**: Always analyze files with care, follow secure practices, and dig into suspicious details to uncover the truth. 🕵️‍♂️🔐  

# Using-tools-like-John-the-Ripper-for-password-cracking
## AIM:
To crack password hashes using John the Ripper in Kali Linux.
## REQUIREMENTS:
- **Operating System:** Kali Linux / Ubuntu / Windows (with JtR binaries)
- **Tools:**
    - John the Ripper (Community/Pro version)
    - Hash generating tools (e.g., openssl, unshadow)
- **Test Data:**
    - /etc/shadow file (Linux hashed passwords)
    - Custom password-protected file (ZIP, RAR, etc.)
## ARCHITECTURE DIAGRAM:
```mermaid
flowchart TD
    A[Password Protected File / Hash] --> B[John the Ripper]
    B --> C[Select Attack Mode: Dictionary or Brute Force]
    C --> D[Load Wordlist / Charset Rules]
    D --> E[Password Cracking Process]
    E --> F[Recovered Passwords]
```
## DESIGN STEPS:
### Step 1: Install John the Ripper
```bash
sudo apt update
sudo apt install john -y
```

### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:
```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:

Step 1: Create a Text File

Right-click on the Desktop and choose Create Document → Empty Document.

Name the file: priya.txt

<img width="471" height="320" alt="Screenshot 2026-05-26 205653" src="https://github.com/user-attachments/assets/904dc774-7e8b-4a2f-adf6-b0e353ef8521" />

Open it and type:

<img width="864" height="649" alt="Screenshot 2026-05-26 205754" src="https://github.com/user-attachments/assets/02ee2fa3-81d4-401f-97b0-5a5356553db0" />

Save and close the file.

Step 2: Create a Password-Protected ZIP File

Right-click on priya.txt → Create Archive.

<img width="474" height="552" alt="Screenshot 2026-05-26 205915" src="https://github.com/user-attachments/assets/d6ddde8f-da87-4c7d-b9df-36a11244c9c0" />

Select .zip format.

Click Other Options, set a password (e.g., 1234), then click Create.

<img width="726" height="423" alt="Screenshot 2026-05-26 210040" src="https://github.com/user-attachments/assets/782909f1-e32b-44a4-94b8-ae18d6463179" />

A file named priya.txt.zip will appear.

Step 3: Open John the Ripper Terminal in Kali Linux

Click on the Kali menu or press the Super (Windows) key.

Search for “john” and click it — this opens the terminal with John the Ripper installed.

<img width="502" height="184" alt="Screenshot 2026-05-26 213701" src="https://github.com/user-attachments/assets/4020decb-fbf8-46a5-8420-216fa836eef6" />

Or simply open a Terminal from the dock or desktop.

Step 4: Navigate to the File Location

In the terminal, switch to the Desktop where the ZIP file is located:

<img width="554" height="552" alt="image" src="https://github.com/user-attachments/assets/84c4ff34-b771-428d-96a6-423d5c74dede" />

Step 5: Confirm the ZIP File is Present

Run: “ls” command

<img width="213" height="55" alt="image" src="https://github.com/user-attachments/assets/deef6fcb-e61e-4a3f-8c8a-ac500b3a1eae" />

You should see priya.txt.zip listed.

Step 6: Generate Hash Using zip2john

Execute:

<img width="295" height="87" alt="image" src="https://github.com/user-attachments/assets/465ddb58-868e-4bce-b20c-73f40c89cc2e" />

Step 7: Verify the Hash File (Optional)

Open hash.txt to ensure it contains the hash line.

<img width="792" height="623" alt="Screenshot 2026-05-26 211139" src="https://github.com/user-attachments/assets/5b6ece61-83a9-41e1-b841-ea44b68f76b5" />

Step 8: Start Cracking the Password

Run:

<img width="744" height="287" alt="image" src="https://github.com/user-attachments/assets/78c7cc23-c13b-4ce6-b8c0-132359d9607a" />

Step 9: View the Cracked Password

After cracking is complete, reveal the password using:

<img width="555" height="158" alt="image" src="https://github.com/user-attachments/assets/5a022ef4-abae-4aee-9831-8006917f0608" />

Step 10: Result
The terminal will display the filename and its cracked password.

## RESULT:
The password hashes were successfully cracked using John the Ripper.


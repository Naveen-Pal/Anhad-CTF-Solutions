
### **The Hidden Image**  
**Forensics Challenge**  
**Points: 50**

You’re a secret agent working on a high-priority mission. A recent raid on a known terrorist training facility turned up empty—no suspects, no weapons. It's as if they knew you were coming. But your team did find a clue: an SD card containing a single, blurry image of the suspected leader.

At first glance, it seems like nothing. But your instincts say otherwise. Something is hidden in that image—something that could explain how the terrorists escaped and what they’re planning next.

[mmi.jpg](./mmi.jpg)

> **Your Objective:**  
Analyze the image and extract any hidden data or messages it may contain.

---

### **Recruitment Portal**  
**OSINT Challenge** 
**Points: 60**

Thanks to your analysis of the image, the field team successfully intercepted and captured a key figure: the organization's recruiter. Under interrogation, he revealed a critical piece of intel—an IP address linked to a secret recruitment and propaganda website:  
**http://82.25.105.26**

But there’s more: he issued a warning that a large-scale attack is imminent—one that could destabilize the entire nation.

> **Your Objective:**  
Investigate the website. Look beyond the surface. Hidden files, steganography, obfuscated scripts—anything could hold the clue to stopping the next phase of the operation.

---

### **The Encrypted Truth**  
**Cryptography Challenge**  
**Points: 70**

Your team uncovered a hidden plain-text file buried deep in the compromised server. It’s named **payload.enc**, and contains a suspicious encrypted string. There’s no metadata—just raw, unintelligible characters.

From server logs, you find a clue: the encryption involved **four operations**—but their order is unknown.

- Base64 Encoding  
- String Reversal  
- ROT13  
- XOR with 0x42  

[payload.enc](./payload.enc)

> **Your Objective:**  
Try all possible permutations of the operations to decode the message. The decrypted content might contain the next critical lead.
---

### **The Binary Clue**  
**Reverse Engineering Challenge**  
**Points: 80**

As the operation unfolds, a hidden file on the recruitment server stands out: an obfuscated binary named **main**. It’s not referenced by the website, nor does it serve any apparent purpose.

Clearly, it was hidden intentionally.

This binary could contain hardcoded secrets, embedded messages, or hidden data. It might even trigger or reveal the group’s plans.

[main](./main)

> **Your Objective:**  
Reverse-engineer the binary. Extract any information it holds—coordinates, names, activation codes, or communications.
---

### **The Final Node**  
**Pwn Challenge**  
**Points: 100**

You’ve finally done it. Inside the binary, you find a secret IP and port combination used for covert communication:

**IP:** 82.25.105.26  
**Port:** 1337

Your team establishes a secure link to the endpoint—and what you uncover is shocking. It's a full-fledged **Command & Control** (C2) server. Real-time messages are being exchanged. Systems across the globe are reporting in.

This is the digital heart of the operation.

> **Your Objective:**  
Infiltrate the server. Crack the interactive shell. Find and extract the final **flag**—the shutdown phrase that can terminate the entire network.

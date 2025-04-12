# AnhadCTF Writeup

## Q1: Forensics
**Challenge:** Analyze the provided image to extract the flag.  
**Solution:**
1. Use `foremost` to carve out files from the image.
   ```bash
   foremost -i image.jpg -o output_directory
   ```
2. Locate the extracted ZIP file in the output directory and extract it.
3. Inside the extracted files, find `code.txt` containing the flag.  
**Flag:** `shadowCTF{MTY=}`

---

## Q2: OSINT
**Challenge:** Investigate the given IP address to find the flag.  
**Solution:**
1. Visit `http://82.25.105.26`.
2. Inspect the website's cookies using browser developer tools (e.g., Chrome DevTools).
3. Locate the cookie named `key` with flag as its value.  
**Flag:** `shadowCTF{QXBy}`

---

## Q3: Cryptography
**Challenge:** Decode the XOR and ROT13-encoded payload.  
**Solution:**
1. **XOR with 0x42:** Decode the hex-encoded payload using XOR key `0x42`.
   ```python
   payload = b"\x0e,\x082 ,\x17%\x1b/!%\x18\x15*+ \x01\x00w'\x15v%\x18,\x1b%$\x16s\x0b\x11p{,\x17q2\x05's\x0c\n\x17\x052+!\x15ws\x18+\x001!,%%!,\x14,\x0b\n\x08t\x0b\x05&+&\x01\x00-\x1b/5% \n.w /\x04p\x175\x7f\x7f"
   decoded = bytes([b ^ 0x42 for b in payload])
   print(decoded.decode())  # Output: ".rinu bg ehbl yyn fv }=HKogSzF{SGPjbqnuf lrx rug rz gbt hbl lyynavS"
   ```
2. **ROT13:** Apply ROT13 to the result.
   ```
   .evah ot ruoy lla si }=UXbtFmS{FTCwodahs yek eht em tog uoy yllaniF
   ```
3. **Reverse the String:** Reverse the final string to get the flag.  
**Flag:** `shadowCTF{SmFtbXU=}`

---

## Q4: Reverse Engineering
**Challenge:** Reverse the provided ELF binary.  
**Solution:**
1. Open the binary in `gdb`.
   ```bash
   gdb ./challenge.elf
   ```
2. Disassemble the `main` function to find the `decode_flag` call.
   ```gdb
   (gdb) disassemble main
   ```
3. Set a breakpoint after `decode_flag` and inspect the result variable.  
**Flag:** `shadowCTF{R2FuZGhpTmFnYXI=}`

---

## Q5: Pwn
**Challenge:** Gain root access on the target server.  
**Solution:**
1. **Decode Previous Flags:**
   - `MTY=` → `16`
   - `QXBy` → `Apr`
   - `SmFtbXU=` → `Jammu`
   - `R2FuZGhpTmFnYXI=` → `GandhiNagar`

2. **Netcat to the Server:**
   ```bash
   nc 82.25.105.26 1337
   ```
3. **Login with Credentials:**
   - Username/Password: `16AprJammuGandhiNagar`

4. **Privilege Escalation:**
   - Navigate to `/home` and find a SUID binary.
   - Execute the binary to spawn a root shell.
   ```bash
   /home/ctfuser/leaky/i_m_here
   ```
5. **Read the Root Flag:**
   ```bash
   cat /root/flag.txt
   ```  
**Flag:** `shadowCTF{Pr1v1l3g3_3sc4l4t10n_ftw!}`



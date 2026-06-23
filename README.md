Simple XOR Password Manager
To whomever is reading this, I am sorry in advance for my spaghetti.

This is a simple password manager I wrote in Python. It is meant to be secure as long as you understand the limitations and risks. It uses XOR encryption combined with PBKDF2‑HMAC‑SHA256 for key stretching. The goal is to keep things simple while still providing real encryption, but you must use it carefully.

Read everything below before using it.

READ ME
If either data file is missing or empty, this program will re‑initialize and wipe everything in there.

If you enter the wrong master password and choose to EDIT, it will decrypt garbage and you will overwrite your vault with garbage.

This program does not verify passwords. If you forget your master password, your data is effectively gone.

Use at your own risk.

Do not store anything important unless you fully understand how this works and accept the risks.

ASCII only. No emojis or special characters. If you use anything outside basic ASCII, the encryption breaks. K.I.S.S. Keep it simple, stupid.

Feel free to take this, edit it, and repost better versions. This is a learning project that can be improved.

What This Program Does
Creates a directory at ~/password_manager/

Stores two files:

password_manager.txt (your XOR‑encrypted data)

key_data.txt (your encrypted XOR key and salt)

Asks you to create a master password on first run

Lets you view or edit the stored text

Re‑encrypts everything every time you read or edit it

Uses PBKDF2‑HMAC‑SHA256 to derive a key from your password

Uses XOR to encrypt and decrypt the text

Uses a new random salt and new random XOR key every time it saves

How It Works (Simple Explanation)
You enter a master password.

A random salt is generated.

PBKDF2 uses your password and the salt to generate a key.

A random XOR key is generated for your text.

The XOR key is encrypted using the PBKDF2 output.

Your text is XOR‑encrypted using the XOR key.

Both encrypted pieces are saved to disk.

This is not enterprise‑grade cryptography, but it is real encryption and will protect your data as long as you use it correctly.

Limitations and Cautions
No password verification

Wrong password during edit will destroy your data

Missing or empty files will trigger a full reset

ASCII only

Not designed for large amounts of data

Not designed for syncing across devices

Not designed to recover forgotten passwords

This is meant to be secure within its design, but it is still a simple tool. Treat it with caution.

Running It
Run the script with Python:

Code
python password_manager.py
On first run, it will ask you to create a master password and enter the initial text you want to store.

After that, you can choose to open the password manager, read the stored text, or edit it.

File Locations
Your encrypted vault files are stored here:

Code
~/password_manager/password_manager.txt
~/password_manager/key_data.txt
These files are created automatically.

Why I Made This
I wanted to learn:

basic encryption

XOR operations

PBKDF2 key stretching

file handling

simple secure storage

how to build something functional from scratch

This project helped me understand how encryption works at a low level while still being practical.

Contributing
If you want to improve this, go ahead.
If you want to rewrite it properly, go ahead.
If you want to make a more secure version, go ahead.

This is a learning project, but it is meant to be secure within its limits.

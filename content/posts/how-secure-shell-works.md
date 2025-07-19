+++
date = '2025-07-18T14:00:00+03:00'
draft = false
title = 'How Secure Shell Works (SSH)'
tags = ["Ssh", "Linux"]
+++

SSH (Secure Shell) is a cryptographic network protocol used to securely connect to remote systems over an unsecured network. It’s commonly used for managing servers, accessing network devices, and transferring files securely. Here’s a simple breakdown of how it works:

### 1. **Client and Server**

* **Client**: The system trying to access another system remotely. Usually, you run an SSH client (like `ssh` on Unix/Linux or PuTTY on Windows).
* **Server**: The remote system that the client wants to connect to, which runs an SSH server (like `sshd` on Unix/Linux).

### 2. **Initiating the Connection**

* When you try to connect to a remote system using SSH, the client sends a request to the SSH server on a specific port (usually port 22).
* The server then responds by sending its public key to the client.

### 3. **Key Exchange and Authentication**

* **Key Exchange**: The client and server exchange encryption keys to establish a secure communication channel. They use algorithms like Diffie-Hellman or Elliptic Curve Diffie-Hellman (ECDH) for this. This ensures that even if someone is eavesdropping on the connection, they won’t be able to decrypt the data.
* **Server Authentication**: The client checks the server’s public key to ensure it is connecting to the right system. This prevents Man-in-the-Middle (MITM) attacks.
* **Client Authentication**: The client must authenticate itself to the server. There are two main ways to do this:

  1. **Password-based authentication**: The client provides a password to authenticate itself.
  2. **Key-based authentication**: The client uses a pair of cryptographic keys—public and private keys. The public key is stored on the server, and the private key remains with the client. The server sends a challenge to the client, which can only be answered correctly by the private key holder, ensuring secure authentication.

### 4. **Encrypted Communication**

* Once authentication is successful, both the client and the server agree on a shared symmetric encryption key that will be used for the session.
* From this point onward, all data exchanged between the client and the server is encrypted using this shared key, ensuring confidentiality and integrity.

### 5. **Session Termination**

* Once the task is complete, the client can disconnect from the server, and the SSH session is terminated. The session key used for encryption is discarded, ensuring that future sessions require fresh key exchanges.

### Key Components of SSH:

* **Public Key Cryptography**: Used for both server authentication and client authentication (when using key pairs).
* **Encryption**: Ensures that all communication between the client and server is secure and cannot be easily intercepted or tampered with.
* **Integrity**: Ensures that the data is not altered during transmission.

### SSH Use Cases:

* **Remote Login**: The most common use case—logging into a remote system to manage it.
* **File Transfer**: Tools like `SFTP` (SSH File Transfer Protocol) and `SCP` (Secure Copy Protocol) allow secure file transfer over SSH.
* **Port Forwarding**: SSH can be used to forward network traffic securely from one system to another, which is helpful in tunneling.
* **Automation/Scripts**: SSH is widely used in scripts and automation for managing remote servers, like in DevOps or system administration.

In essence, SSH provides a secure way to manage remote systems by using encryption to protect the data being transmitted and ensuring both the client and server are properly authenticated.
---
layout: post
title:  "SSH Login Using Public Key Authentication"
date:   2018-09-28 16:42:29 -0400
categories: ssh server linux
tags: ssh
author: Ryan Angelo
---

The following process allows a user to login from a client machine to a remote machine (which we will hereby refer to as server) without using a password, but rather with public key authentication.

1 - Create the RSA Key Pair

The first step is to create the key pair on the client machine. This is the machine that you are going to be using to connect to the remote servers. In a terminal on the client machine, enter the following command:

```sh
ssh-keygen -t rsa
```

2 - Store the Keys and the Passphrase

Once you have entered the key gen command, you will be prompted with a few more questions:

Enter file in which to save the key (/home/<your_username>/.ssh/id_rsa):
You can press enter here, saving the file to the specified user home directory.

Enter passphrase (empty for no passphrase):
It is your choice as to whether or not you want to include a passphrase. The benefit is that there is the added security in the situation where the private key is compromised. The person who obtained the private key would also need the passphrase in order to utilize the private key. However, this also means that you, as the legitimate user will also require the passphrase in order to utilize the key, unless you use ssh-agent to store the password.

The entire key generation process appears as follows:

```sh
ssh-keygen -t rsa
```

Enter file in which to save the key (/home/<your_username>/.ssh/id_rsa): 

Enter passphrase (empty for no passphrase): 

Enter same passphrase again: 

Your identification has been saved in /home/<your_username>/.ssh/id_rsa.

Your public key has been saved in /home/<your_username>/.ssh/id_rsa.pub.

The key fingerprint and random art image is then displayed.

The public key is now located in /home/<your_username>/.ssh/id_rsa.pub The private key, which serves as your identification, is now located in /home/<your_username>/.ssh/id_rsa

3 - Copy the Public Key to the Target Server

Once the key pair is generated, we need to place the public key on the server that we want to be connecting to from the client system that we generated the keys on.

You can copy the public key that was generated on the client system to the remote server using ssh with the following command. (Make sure the place the username with your username on the server, and the IP address with the server's IP address. 

```sh
cat ~/.ssh/id_rsa.pub | ssh <your_username>@111.222.3.4 "mkdir -p ~/.ssh && cat >>  ~/.ssh/authorized_keys"
```

Alternatively, you can copy the public key into the server's authorized_keys file with the ssh-copy-id command. Again, make sure to replace the example username and IP address.

```sh
ssh-copy-id <your_username>@111.222.3.4
```

Both of these options will copy the public key from the client machine to the server's authorized_keys file. You should now be able to ssh from the client system to the server using the public key authentication mechanism. If you did not require a passphrase in your key generation, then you will now be able to login to the server from the client without using a password.

Additional information regarding using Public Key Authentication with OpenSSH is available on the Ubuntu website: https://help.ubuntu.com/community/SSH/OpenSSH/Keys
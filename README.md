# Deploying the server to Digital Ocean

Go to Digital Ocean and create a droplet

If you don't have an account, you can get free 100$ by registering to Digital Ocean via this link: https://m.do.co/c/402f87d0c72e

## Creating the SSH KEY in UBUNTU

Move into .ssh directory

```bash
$ cd ~/.ssh
```

Generate ssh key

```bash
$ ssh-keygen
```

List the files with a regular expression (fsfe2 is my ssh key name)

```bash
$ ls | grep fsfe2
```

ffse2 <- private key

fsfe2.pub <-public key

## SSH into server

```bash
$ ssh root@YOUR_IP
```

If the permission is denied

```bash
$ ssh -i fsfe2 root@YOUR_IP
```

You need to pass the name of the private key to the server. In my case it was "fsfe2"

To debug and get more information use

```bash
$ ssh root@YOUR_IP -v
```

## Activating the keychain

```bash
$ sudo nano ~/.ssh/config
```

Switch this two properties to "yes"

```text
Host *
 AddKeysToAgent yes
 UseKeychain yes
```

## Add private key to keychain

```bash
$ ssh-add -K ~/.ssh/fsfe2
```

## Switching out of root

For example:

root@ubuntu-s-143v-sfo2:~#

"#" means you are on a Root / Super User

You can cheak if you really are the root by typing

```bash
$ whoami
```

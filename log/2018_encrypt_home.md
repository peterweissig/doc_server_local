# 2018 encrypt home

[go back to general config](../doc/general.md#encryption)


## Info
https://askubuntu.com/questions/1029249/how-to-encrypt-home-on-ubuntu-18-04


## Steps
To encrypting an existing users home dir.


### 1. logout
logout and log into an admin account

### 2. install encryption utilities
From that launchpad bug, ecryptfs-utils is now in the universe repo.

~~~~~
    $ sudo apt install ecryptfs-utils cryptsetup
~~~~~

### 3. migrate the home folder
#### a) migrate

~~~~~
    $ sudo ecryptfs-migrate-home -u <user>
        # followed by user password of that account
~~~~~

#### b) unwrap passphrase
Then logout and login into the encrypted users account - **before a reboot!** - to complete the encryption process.

Inside the account print and record the recovery passphrase:

~~~~~
    $ ecryptfs-unwrap-passphrase
~~~~~

### 4. login
You can now reboot and login. Once you are satisfied you can delete the backup home folder.


## Encrypt home of new user
Also if you want to create a new user with encrypted home dir:

~~~~~
    $ sudo adduser --encrypt-home <user>
~~~~~

For more info:
* man ecryptfs-migrate-home
* man ecryptfs-setup-private

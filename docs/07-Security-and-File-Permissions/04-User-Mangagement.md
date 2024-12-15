# USER MANAGEMENT

- Take me to the [Tutorial](https://kodekloud.com/topic/user-management/)
- In this lecture we will learn how to create and manage user accounts in Linux.

#### User Add

- To create a new local user **`bob`** in the system use **`useradd`** command.

  ```bash
  [~]$ useradd bob
  ```

- To get more details about **`bob`** account like, home director, uid, and shell use **`/etc/passwd`**

  ```bash
  [~]$ grep -i bob /etc/passwd
  bob:x:1002:1002::/home/bob:/bin/sh
  ```

  ![useradd](../../images//useradd.PNG)

- To check the uid or username of the user logged in user **`whoami`** command.

  ```bash
  [~]$ whoami
  bob
  ```

- All user's password are store under **`/etc/shadow`**

  ```bash
  [~]$ grep -i bob /etc/shadow
  bob:!:18341:0:99999:7:::
  ```

- To change the password of current user use **`passwd`** as shown below

  ```bash
  [~]$ passwd 
  Changing password for user bob.
  New UNIX password:
  Retype new UNIX password:
  passwd: all authentication tokens updated
  successfully.
  ```
  or for any specific user use **`passwd <username>`** as shown below
  ```bash
  [~]$ passwd bob
  Changing password for user bob.
  New UNIX password:
  Retype new UNIX password:
  passwd: all authentication tokens updated
  successfully.
  ```

# Managing Users

- **`useradd`** command be used along with many attributes as show below.

  ```bash
  [~]$ useradd -u 1009 -g 1009 -d /home/robert -s /bin/bash -c ”Mercury Project member" bob
  ```

  ![manage](../../images//manage.PNG)

  where:
- `-c` custom comments
- `-d` custom home directory
- `-e` expiry date
- `-g` specific GID
- `-G` create user mwith multiple seconday groups
- `-s` specify login shells
- `-u` specific UID

- To confirm that the user was create successfully, we can check that using
  ```bash
  [~]$ id bob
  uid=1009(bob) gid-1009(avenger) groups=1009(avenger)
  ```
- To confirm that the special comments were created, we can inspect the password file
  ```bash
  [~]$ grep -i bob /etc/passwd
  bob:x:1009:1009:Mecury Project Member:/home/robert:/bin/bach
  ```


- To delete a user use **`userdel`** command

  ```bash
  [~]$ userdel bob
  ```

- To add a new linux group and specify the *GID* use **`groupadd`** command

  ```bash
  [~]$ groupadd –g 1011 developer
  ```

- To delete a group user **`groupdel`** command

  ```bash
  [~]$ groupdel developer
  ```

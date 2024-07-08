##### bandit0
- `pass : bandit0`
- Connecting to **bandit.labs.overthewire.org** at port 2220
- cat a file

##### bandit1  
`pass : NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL`

- cat the file "`-`"
```bash
cat ./-
```

##### bandit2
`pass : rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi`

- cat this file 
```bash
cat "spaces in the filename"
```

##### bandit3
`pass : aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`

- Cat a hidden file
```bash
cat .hidden
```

##### bandit4
`pass : 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe`

- Find flag in this
![[Pasted image 20240115112605.png]]

- Use file command over all files , only one file will have a ascii text which contains flag
```bash
file ./file*

cat ./-file07
```

##### bandit5
`pass : lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`

- Find a file in these folders which contains exactly 1033 bytes of data
![[Pasted image 20240115115611.png]]

```bash
 find . -type f -size 1033c

- `c`: bytes
- `k`: kilobytes
- `M`: megabytes
- `G`: gigabytes
```

bandit6
`pass : P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU`

Find a file where
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

```bash
find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
```

##### bandit7
`pass : z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S`

- The password for the next level is stored in the file **data.txt** next to the word **millionth**

```bash
cat data.txt | grep millionth
```

##### bandit8
`pass : TESKZC0XvTetK0S9xNwm25STk5iWrBvP`

- The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once
```bash
sort data.txt| uniq -u

-u : prints only unique lines
```


bandit9
`pass : EN632PlfYiZbn3PhVK3XOGSlNInNE00t`

- The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

```bash
strings data.txt | grep =
```

##### bandit10
`pass : G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s`

The file has password , but it is base64 encoded
```bash
cat data.txt | base64 -d
```


##### bandit11
`pass : 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM`

- File contains password, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

```bash
cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'
```

##### bandit12
`pass : JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv`

-  **data.txt** file is given , which is a hexdump of a file that has been repeatedly compressed.

```bash
xxd -r data.txt > data

-r gives the actual file from the hexdump

then the file is recursively decompressed to get the flag.
```

##### bandit13
`pass : wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw`

- the password for bandit14 is stored in /etc/bandit_pass/bandit14
- but this file can be accessed only if the user logged in is bandit14
- but to login as bandit14 we are given ssh key.
- first we login as bandit14 using ssh key , then view the password for bandit14 stored there.

```bash
As user bandit13
	ssh bandit14@localhost -i sshkey.private -p 2220


As user bandit14
	cat /etc/bandit_pass/bandit14
```

##### bandit14
`pass : fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq`

- Submit the password of bandit14 to a service running on 30000 on localhost

```bash
nc localhost 30000

submit password here
```
##### bandit15
`pass : jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt`

- Submit the password of bandit14 to a service running on 30001 on localhost using ssl encryption
- openssl is used to initiate a connection using ssl encryption

```bash
openssl s_client -connect localhost:30001
```

##### bandit16
`pass : JQttfApK4SeyHwDlI9SXGR50qclOAil1`\

- there are multiple ports running between range 31000 to 32000. 
- find which ports are running , and in that find which ports are running using ssl connection 
- and supply current password to it
- it will provide the ssh key
- login as bandit17 obtain the password from /etc/bandit_pass/bandit17

##### bandit17
`pass : VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e`

- There are 2 files in the homedirectory: **passwords.old and passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**

```bash
diff passwords.new passwords.old
```

##### ==bandit18==
`pass : hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg`

- Cant login with the above password bcoz it is throwing us out after logging in
- But description says that the password for bandit19 can be found in the home directory of bandit18 as "readme"
- We are not able to login through ssh , as it will log us out , but we can make it execute some command before throwing us out

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat ~/readme"

outputs the password
```
##### bandit19
`pass : awhqfNnAbc1naukrpqDYcF95h7HoMTrC`

- An executable has setuid bit set by the user bandit20
- so whenever the executable is executed it executes as user bandit20
- so we can read the password file as bandit20 user

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

##### bandit20
`pass : VxCazJaVykI6W36BkBU0mJTCM8rR95XT`

desc : There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

- We'll setup a netcat server on some port 
```bash
echo -n "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | nc -lp 8080 &
```
- the command creates a simple network service that listens on port 1234. When a client connects to this port, the server sends the string/current password to the client.

##### bandit21
`pass : NvEJF7oVjkddltPSrdKEFOllh9V1IBcq`

desc : A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

- Viewing all the cron jobs and digging
![[Pasted image 20240116124502.png]]

- The cron job creates a temporary file in /tmp and then appends the password of bandit22 to that file.
- Viewing the contents of that file , provides the password.


##### bandit22
`pass : WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff`

desc : A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

- Viewing cron.d and digging the file
![[Pasted image 20240116130504.png]]

- From the understanding of the bash script , I tried to bring the result by manually assigning the myname as bandit23
![[Pasted image 20240116130844.png]]

##### ==bandit23==
`pass : QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G`

desc : A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed

- Viewing the cron job
![[Pasted image 20240116142300.png]]

- The script iterates through all the files in the folder `/var/spool/bandit24/foo/` and checks if the owner of the file is bandit23 , if it created by us , then it will executed and then timed out and removed.
- Now we just have to write a script that reads the password of bandit24 , and writes it into a file that can be accessed by us. 
- The script is executed by cronjob of user bandit24 hence it is possible for that to read the password.

Steps to perform:
- We create a temporary folder in /tmp and give it full access
- then write the script in that folder ,give it full access then copy it to foo directory.
- Then we also create a text file called `password_for_bandit24` where the password will be written by the script

![[Pasted image 20240116143416.png]]

![[Pasted image 20240116143344.png]]

![[Pasted image 20240116143555.png]]

- After some time , the script gets executed by cron job , then the password is written into `password_for_bandit24.txt` file

![[Pasted image 20240116143812.png]]

##### bandit24
`pass : VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar`

desc : A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.  
You do not need to create new connections each time

```python
import sys
import socket

bandit24_pass = "VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar"
try:

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect(("localhost", 30002))

    starting_message = client_socket.recv(2048)


    for pincode in reversed(range(9999,0000)):
        message_to_be_sent =bandit24_pass+" "+(str(pincode).zfill(4))+"\n"

        client_socket.sendall(message_to_be_sent.encode())

        received_message = client_socket.recv(1024).decode()

        if "Wrong" in received_message:
            print("Trying...  ",pincode)
        else:
            print(received_message)
            break
finally:
    sys.exit(1)
```

![[Pasted image 20240116201329.png]]

##### bandit25
`pass : p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d`
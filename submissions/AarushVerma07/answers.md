
# level 0 > 1 
thoughts - it was pretty straight forward using cat to read the password     
  key - obtained

# level 1 > 2
thoughts - this one was hard initially as i tried to put the 'dash' in colons first then i had to google the command which allowed to cat special characters like dash or dot   
key - obtained

# level 2 > 3 
thoughts - i was pretty dumb in this one although i knew what format was it i kept writing wrong spelling of the files one instance it was a very small typo that i missed "s" and in the other  one was that i i literally removed the spaces  or in other case i added "the". overall it was easy to solve but my typo made me waste some time   
key - obtained

# level 3 > 4 
thoughts - basic commands nothing much  
key - obtained


# level 4 > 5 
thoughts - i brute forced this one i didn't use find for some reason , maybe it didnt really clicked me and brute forcing wasn't that hard at that moment  
key - obtained


# level 5 > 6 
thoughts - it was pretty much straight forward and the conditions were given on the page itself  
key - obtained


# level 6 > 7
thoughts -  tried using just the 'find' but i was covered with lot of permission denied messages as i didn't have permission for some files (it had searched all directory) then i tried again with routing those messages to null file which made the terminal lot cleaner    
key - obtained

# level 7 > 8 
thoughts -  it was pretty straight forward using grep to get the password by showing up the millionth word  
key - obtained


# level 8 > 9 
thoughts - sort was used first rather than using uniq because uniq shows  duplicates of they right next to each other so two identical lines which would have been lost be uniq is recovered by sort as it rearranges it into alphabetical order and by adding '-u' it showed only the single unique lines rather than the duplicates   
key - obtained


# level 9 > 10 
thoughts - i used sort first as i didnt read the question correctly and i found buch of random jumbled letters flooding my screen then i had to read the question again and found that it had 'human-readable strings' then it clicked me and i used strings instead of sort which worked liek a charm    
key - obtained


# level 10 > 11
thoughts - it was pretty straight forward using base64 encryption, it was decoded thru the in-built decoder   
key - obtained


# level 11 > 12 
thoughts - the text was encoded using the rot13, at the moment i really wanted use an online decoder for rot13 but in the meanwhile i also found way to do it natively on the terminal itself using translate command, it took me while to understand the modifiers but yeah then i was able to use it on the terminal itself   
key - obtained


# level 12 > 13 
thoughts -  it was a fun level to solve, i started it  with recommend action of copying the data file into unique directory. then i copied data file again and and used xxd to decompress the  hexdump file into better form. upon receiving the new file i again checked the type of file it was which turned out to be in gz, i decompressed it using gunzip which then gave another file, i repeated the process until i got the file type as text, which then i used cat to get the password. (i mainly encountered gz, bz2 and tar)  
key - obtained



# level 13 > 14 
thoughts -  so i did understood what the problem was, instead of  relying on the password as usual we had use the file in the bandit13 directory which acted as ssh private key. so i hosted the bandit14 on the local host as it was just another account on the same machine(bandit13) so i used the command "ssh -i ssh.private.key bandit14@localhost -p 2220" then i was aksed to confirm the host fingerprint which i accepted but then it suddenly said that "Could not create directory '/home/bandit13/.ssh' (Permission denied)" followed by "connecting from localhost is blocked" which meant that the ssh wasn't using the private key which i was providing and redirecting to password authentication. then i looked up the claude to get help, to which i got reply that the file permissions might be too loose(bandit13 might have access) which made ssh reject the key, so then i looked up metadata of the key and it clearly said that it was owned by bandit14 also claude said it was following permission 640; i was then asked to tighten the permission to 600 but that didnt work as only owner(bandit14) had the permission to change it. i then further with the help of claude tried to brute force the public-key only authentication which again gave me more error   

error messages -  
1.
```
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit13/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit13/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _ | '_ \ / _ | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames
!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.
backend: gibson-1
Received disconnect from 127.0.0.1 port 2220:2: no authentication methods enabled
Disconnected from 127.0.0.1 port 2220
```
2.
```
-rw-r----- 1 bandit14 bandit13 1679 Jun 14 17:53 sshkey.private
chmod: changing permissions of 'sshkey.private': Operation not permitted
```
3.
```
ssh -i sshkey.private bandit14@localhost -p 2220
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])?yes
Could not create directory '/home/bandit13/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit13/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _ | '_ \ / _ | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames
!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.
backend: gibson-1
Received disconnect from 127.0.0.1 port 2220:2: no authentication methods enabled
Disconnected from 127.0.0.1 port 2220
bandit13@bandit:~$
```
key - not obtained

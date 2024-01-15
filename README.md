# walmart-cicd-15thjan-2024

### How to create ssh-key-pair 

```
[ec2-user@ip-172-31-29-249 ~]$ ssh-keygen 
Generating public/private rsa key pair.
Enter file in which to save the key (/home/ec2-user/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/ec2-user/.ssh/id_rsa.
Your public key has been saved in /home/ec2-user/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:ZVGr7ISJUlkOqE6u5pbuTwcvD2cWaouGyVW27d9HUyw ec2-user@git-linux-server
The key's randomart image is:
+---[RSA 2048]----+
|     .. . ...    |
|    .  =   . .   |
|   .  o . o . .  |
|  o  + . * . E o |
| + .+.+ S +   o  |
|  o.+o.. o   o   |
|ooo* *.   . . .  |
|+*+ X  .  .  .   |
|B=.o .  .. ..    |
+----[SHA256]-----+
[ec2-user@ip-172-31-29-249 ~]$

[ec2-user@ip-172-31-29-249 ~]$ cat  /home/ec2-user/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDP/+w8MdzjuwtaJ66yDYP5fG0hfUvLWIYkveBesWSFoqofbjxCI/n8qS6FYpd1vs0SgdT+jvbziSvIrEk7F6ruVIEJL+2g3J9y1wKxTS6JOG8cMFIULzGgU7rlIWlBAwKopzu/zFUKzeAvNdtb+AFVZGF3BYRAbsxY0vl+5cTt433+Kf31k9RysoTk6L4vyoEdnqQDsFzq1kY6QM35UyXGLieCTn69hz+gMUItjkzPsD6uPqzsf+2p8Rw7bV+KZHeG1l/rHQT+nZD3MMPs2rI7l3rcoKRg8laHc8Q4QYapM2P/0JP3FqiiOWqgXgsscUVcSSmOSc4ItQGKETWOeMgD ec2-user@git-linux-server
[ec2-user@ip-172-31-29-249 ~]$ 




```

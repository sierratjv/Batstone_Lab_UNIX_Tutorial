# Info server
**Do not run programs on the head, which is the place you first login. Login to a node immediately.**

Info server consists a head (called info) and serveral nodes (called info16, info17, info18, ...). Head and nodes are different computers.

Login to head: type ``ssh username@info.mcmaster.ca``. Then type ``password`` (You don't see the characters when you enter the password). Type ``exit`` to leave the server.

Login to nodes, for example, info114: type ``ssh info114``. Then type ``password``. Type ``exix`` to leave the node and go back to the server head. 

In the head, type ``usage`` to get information of how these computers are currently used by people.
```
 Usage script is located in /usr/local/bin 
 Collecting information ... please wait 

info:    13:43:05 up 37 days, 23:20, 11 users,  load average: 0.00, 0.02, 0.05

info16:  13:43:05 up 31 days,  2:52,  0 users,  load average: 0.00, 0.00, 0.00
info17:  13:43:05 up 31 days,  2:54,  1 user,  load average: 0.23, 0.33, 0.27
info18:  13:43:05 up 30 days, 23:01,  1 user,  load average: 0.17, 0.31, 0.37
info19:  13:43:05 up 30 days, 23:01,  0 users,  load average: 0.24, 0.15, 0.10
info20:  13:43:05 up 1 day, 23:47,  2 users,  load average: 0.35, 0.23, 0.09

info113:  13:43:05 up 205 days, 22:50,  5 users,  load average: 0.01, 0.10, 0.07
info114:  13:43:05 up 204 days, 13:16,  3 users,  load average: 0.97, 0.95, 0.91
info115:  13:43:05 up 205 days, 23:01,  6 users,  load average: 31.33, 26.07, 26.98
info2020: 13:40:01 up 584 days, 17:18,  8 users,  load average: 58.73, 57.01, 57.33
```

# Compute Canada/Digital Research Alliance of Canada
## Guides
Beginner video: https://www.youtube.com/watch?v=JY1jo9GRffg&t=290s.

Read the how-to guides on this web page to learn how to transfer files and run jobs: https://docs.alliancecan.ca/wiki/Technical_documentation. 

## clusters
- cedar.computecanada.ca
- graham.computecanada.ca
- narval.computecanada.ca
- niagara.computecanada.ca
- beluga.computecanada.ca

## Apply an account
Apply your account on Compute Canada Data Base (CCDB): https://ccdb.alliancecan.ca/security/login. 

**If you are students, you need a Compute Canada Role Identifier (CCRI) from your professor(s) for application.**

## Login 
Login to login node using, for example, ``ssh username@graham.computecanada.ca``.

Once you login as a student, at your home directory, you will see 3 directories: ``nearline``, ``projects``, ``scratch``. In ``nearline`` and ``project``, you will see you professor name, ``def-batstone``. In ``def-batstone``, you will see each user. 

## Transfer files (``rsync``, ``scp``)
First login to data transfer node from login node using, for example, ``ssh gra-dtn1.computecanada.ca``. 

Transfer files from info server to compute canada server: ``[name@info114 ~]$ rsync -avz --no-g --no-p files username@graham.computecanada.ca:path/to/files``

Use sha256sum check files, run the commands on both servers: ``[name@server ~]$ find path/to/files -type f -print0 | xargs -0 sha256sum | tee checksum-result.info.log`` 

Use ``diff`` to check if there are differences between checksum, no output if no difference: ``diff checksum-result.info.log checksum-result.graham.log``



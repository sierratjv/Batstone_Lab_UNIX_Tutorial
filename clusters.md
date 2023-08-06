# Info 
**Do not run programs on the head, which is the place you first login. Login to a node immediately.**

Info server consists a head (called info) and serveral nodes (called info16, info17, info18, ...). Head and nodes are different computers.

Login to head: type ``ssh username@info.mcmaster.ca``. Then type ``password`` (You don't see the characters when you enter the password). Type ``exit`` to leave the server.

Login to nodes, for example, info114: type ``ssh info114``. Then type ``password``. Type ``exix`` to leave the node and go back to the server head. 

### usage
In the head, type ``usage`` to see how many people are currently using the computers.
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
### top
Type ``top`` to see what jobs are running currently.
```
top - 16:41:15 up 224 days, 16:14,  4 users,  load average: 1.18, 1.11, 1.01
Tasks: 1313 total,   2 running, 1311 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  2.1%ni, 97.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  264632216k total, 224453896k used, 40178320k free,   186608k buffers
Swap:  1052668k total,  1051348k used,     1320k free, 220917416k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
35231 xingyuan  30  10 26808  14m 1428 R 99.7  0.0   0:29.74 glimmer3           
34851 xingyuan  30  10  141m 4668 2968 S  0.7  0.0   0:03.43 wget               
35295 xingyuan  30  10 20172 2456 1104 R  0.7  0.0   0:00.14 top                
 4880 root      20   0  490m 6464 1436 S  0.3  0.0 169:10.42 fail2ban-server    
    1 root      20   0 23600  552  332 S  0.0  0.0   0:06.39 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.42 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:24.32 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:58.70 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 stopper/0          
    6 root      RT   0     0    0    0 S  0.0  0.0   0:17.39 watchdog/0         
    7 root      RT   0     0    0    0 S  0.0  0.0   0:20.17 migration/1        
    8 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 stopper/1          
    9 root      20   0     0    0    0 S  0.0  0.0   0:49.50 ksoftirqd/1        
   10 root      RT   0     0    0    0 S  0.0  0.0   0:18.08 watchdog/1         
   11 root      RT   0     0    0    0 S  0.0  0.0   0:13.32 migration/2        
   12 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 stopper/2          
   13 root      20   0     0    0    0 S  0.0  0.0   0:38.90 ksoftirqd/2        
```
# Compute Canada/Digital Research Alliance of Canada
**Watch this beginner video https://www.youtube.com/watch?v=JY1jo9GRffg&t=290s.**

**This is the document of how to use the clusters https://docs.alliancecan.ca/wiki/Technical_documentation.**

## clusters
- cedar.computecanada.ca
- graham.computecanada.ca
- narval.computecanada.ca
- niagara.computecanada.ca
- beluga.computecanada.ca

## Apply an account
Apply your account on Compute Canada Data Base (CCDB): https://ccdb.alliancecan.ca/security/login. 

**If you are a student, you need a Compute Canada Role Identifier (CCRI) from your professor for application.**

## Login 
Login to login node using, for example, ``ssh username@graham.computecanada.ca``.

Once you login as a student, at your home directory, you will see 3 directories: ``nearline``, ``projects``, ``scratch``. In ``nearline`` and ``project``, you will see you professor name, ``def-batstone``. In ``def-batstone``, you will see each user. 

## Transfer files (``rsync``, ``scp``)
First login to data transfer node from login node using, for example, ``ssh gra-dtn1.computecanada.ca``. 

Transfer files from info server to compute canada server: ``[name@info114 ~]$ rsync -avz --no-g --no-p files username@graham.computecanada.ca:path/to/files``

Use sha256sum check files, run the commands on both servers: ``[name@server ~]$ find path/to/files -type f -print0 | xargs -0 sha256sum | tee checksum-result.info.log`` 

Use ``diff`` to check if there are differences between checksum, no output if no difference: ``diff checksum-result.info.log checksum-result.graham.log``

## Run jobs
Write your job in a script, and use ``sbatch`` to submit job.
```
sbatch simple_job.sh
```
The script looks like:
```
#!/bin/bash
#SBATCH --time=00:15:00
#SBATCH --account=def-someuser

commands you want to run
```

## Check jobs status
**sq**

Type ``sq`` to get the job ID and status (ST) of your jobs:
```
JOBID       USER              ACCOUNT           NAME  ST  TIME_LEFT NODES CPUS TRES_PER_N MIN_MEM NODELIST (REASON) 
7383005    sux21     def-batstone_cpu        test.sh  PD      10:00     1   32        N/A     10G  (Priority) 
```
**seff**

Type ``seff jobID``:
```
Job ID: 7545708
Cluster: graham
User/Group: sux21/sux21
State: PENDING
Cores: 1
Efficiency not available for jobs in the PENDING state.
```


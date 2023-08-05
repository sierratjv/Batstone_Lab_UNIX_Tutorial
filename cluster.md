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


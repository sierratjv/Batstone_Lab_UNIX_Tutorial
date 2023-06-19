# Compute Canada/Digital Research Alliance of Canada
## Resources for learning
Watch this video: https://www.youtube.com/watch?v=JY1jo9GRffg&t=290s.

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

Use ``diff`` to check if there are differences between checksum, no output if no difference: ``diff checksum-result.info.log checksum-result.graham.log`



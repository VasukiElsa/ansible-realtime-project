TASK 1 :
----
Create Three EC2 Instance in AWS using ansible loops. And two instances with ubuntu and one instance with amazon-linux OS
---

TASK 2 :
---
Setup passwordless authentication between control nodes and newly created ec2-instances
---

TASK 3 :
---
Automatically shutdown the ubuntu machines using ansible-condition(when)
---

IMPLEMENTING :
---
TASK 1
Our control node act as a localhost and python modules on installed on control nodes and we create ec2-instances on AWS by not using SSH protocol, because AWS is not understand those protocols. The only way to create resources is by talking to the aws - API(Application Programming Interface). Using Boto3 python module we talk to the aws-api. Using ansible-collection modules we implement this infrastructuring tasks on aws.

Dependencies:
---
python >= 3.6
boto3 >= 1.28.0
botocore >= 1.31.0

Install boto3 and ansible-collections:
---
$ pip3 install boto3
$ ansible-galaxy collection install amazon.aws

---

TASK 2
---
Setup a passwordless authentication using ssh-copy-id

$ssh-keygen (make sure to generate public-private secret key)
#To see the ssh generated keys go ~/.ssh/ directory

$ ssh-copy-id  -f "-o IdentityFile /path-to-pem-file" user-name@Instance-public-key
(Here we are copying ssh public key to the remote server)

---

TASK 3
---
Using ansible-builtin-command module, we shutdown the debian family by using "when" condition.


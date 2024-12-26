# Jenkins Master Slave Architecture SetUP:
Jenkins Master-Slave cluster for Linux OS on the top of AWS Cloud

I use AWS EC2 instances for this architecture :

  - "The slave type is permanent Slave and Operating System is Linux".
  - Distributed Scheduling cluster

Overview of Steup :

1.  I use aws Cloud EC2 (AMI-amazon linux2) for -> Master node on which i Install jenkins.
2.  For Slave i also same EC2 instance and connection by SSH .
3.  I use jenkins by webUI using public IP of instance and **jenkins port no:8080**.

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/9d0be42d-61e2-42bb-94f1-199548561e8a)


Note:

  For Adding Slave Node to jenkins follwing things need to do:
  -  java must installed on that Slave because jenkins made from java.
  -  SSH should be enable in that Slave.
  -  Jenkins Agent installed on that Slave.
  -  Jenkins Slave node store data by default on slave so we need to create Directory on Slave node for data store.


## On Slave Node EC2 terminal (For Linux OS): 
Install java on Slave: 

      sudo yum install java-17-amazon-corretto-devel

Now create Directory for workspace:

       mkdir PSworkspace

 ![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/ab75199b-cbec-426a-8718-ab9f12a28579)

## On Jenkins webUI :

### Step-1: [Click manage Jenkins and then Node option on jenkins webUI]

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/7db4e9d4-0d3b-4307-b787-801a584f4572)

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/bf767e21-de1c-4ef2-bd9d-51b3ddd41fad)

### Step-2: [Create New Node, Create Node named as 'psSlaveNode']

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/99cb4cca-b3f5-446e-8d3b-03e5c812c98e)

### Step-3: [Now Fill information about slave]

Label : It helps to execute job on which slave Node by Label name of Slave.

Remote root directory : This Slave Location we created for store data of job on slave.

Number of executors: Jenkins job execute with help of Build Executors, It menas If Build Executor is 3 then 3 Job run at a time or concurrent on that SlaveNode.
    
   ![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/9cded8e7-f45c-44c2-89a3-e9f3abb82a8f)

### Step-4:
Select "Launch method" is -->>  "Launch agent by via SSH"  ( Thsi is because we use linux os system and jenkins required agent download by SSH and Connect Master by SSH to SlaveNode.)

In "Host" -->> Fill public Ip of Slave Node

And select "Credentials" -->> ADD
    
![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/ed202d02-64f6-499c-b5c9-a703d64b74ac)

### Step-5:  (In Credentials)
In "Kind" -->> "SSH username and private key"

- Note:

The private key which is used during launch Slave Node that key download on Local machine open that key by Double tap and copy that key and paste in "private Key" option 
  
![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/cacf59c5-97d6-40ef-a76f-56201caa805e)

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/b7162b47-11c6-47c6-b3d4-b0dad78ba6a6)

- Host verification means When we connect any system by SSH 1st time they ask Yes or No so we select Non-verification strategy.

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/78d19d95-c506-4596-962c-d89bd0a9deda)

Now Slave is Connected to master :

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/7da32573-3afb-4ef4-b45a-01c7bbbcb71c)

### Create Small job which is run on Slave for testing:
Create "New item" and select Freestyle job.

In general there is option for select this job on which Slave execute and add here label which given to slave.

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/b4a4c3cc-985e-48bd-aa5f-000474ca6593)

In "Build" in Execute shell (Because linux os have Shell) and add any command .

Note: 

 The command should be use sudo for admin power and intractive command give arguments otherwise job fails.

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/bd5c2825-5b59-48ae-b043-1c6a508b7ea5)

 Build job :

 we see details on console output of that job 

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/b2c02dde-86de-4009-b96e-117bc487bb89)

We can also check on EC2 terminal of slave Node:

- before:

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/7653c668-4887-4565-950c-322ab29b21d0)

- After job execute git installed:

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/1ea91c4f-71c7-4148-b56f-80d6ba033b74)

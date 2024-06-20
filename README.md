# Jenkins-Master-Slave
jenkins Master-Slave cluster for Linux OS 

We use AWS ec2 instances for this architecture :

  - "The slave type is permanent Slave and Operating System is Linux".
  - Distributed Scheduling cluster

Overview of Steup :

1.  I use aws Cloud EC2 (AMI-amazon linux2) for -> Master node on which i Install jenkins.
2.  For Slave i also same EC2 instance and connection by SSH .
3.  I use jenkins by webUI using public IP of instance and jenkins port no:8080.

![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/9d0be42d-61e2-42bb-94f1-199548561e8a)


Note:

  For Adding Slave Node to jenkins follwing things need to do:
  -  java must installed on that Slave because jenkins made from java.
  -  SSH should be enable in that Slave.
  -  Jenkins Agent installed on that Slave.
  -  Jenkins Slave node store data by default on slave so we need to create Directory on Slave node for data store.


✧ On Slave Node EC2 terminal (For Linux OS) : 
  
  Install java on Slave 

       # sudo yum install java-17-amazon-corretto-devel

  Now create Directory for workspace

       # mkdir PSworkspace


 ![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/ab75199b-cbec-426a-8718-ab9f12a28579)


 ✧ On Jenkins webUI :

  Go nodes on jenkins webUI

  ![image](https://github.com/Pratikshinde55/Jenkins-Master-Slave/assets/145910708/7db4e9d4-0d3b-4307-b787-801a584f4572)

 
 

    


   


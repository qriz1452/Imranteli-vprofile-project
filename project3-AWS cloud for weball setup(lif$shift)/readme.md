
In project 1 we have used vagrant to provision resources and after privsioning we have ssh and installed n configured services .

In project 2 we have used only vagrant to up the whole stack , we created scripts for each service and modified a vagrant file to provision the resourceses using those scriopts so it is Fully IAC.



-----------------

Project 3 : lift and shift to AWS 
----------------
![image](https://github.com/qriz1452/Imranteli-vprofile-project/assets/112246222/30e9bb44-e0e9-4e3a-9abd-13f7e7b43eb9)


![image](https://github.com/qriz1452/Imranteli-vprofile-project/assets/112246222/506e97f9-cdba-4c7d-a87f-28697c66ccf4)


Problem : 
Complex management
Scale up / down complexity
upfront capex and regular opex
manual process
difficult to automate
time consuming

Solution :
cloud setup
payg
IAAS
flexibility
automation

----

AWS Services used in thsi project  :
EC2   ------  VM for tomcat  , rabbitmq,  memcache , mysql
ELB   ------   nginx LB replacement
Autoscaling   -------   automation for vm scaling
s3 /efs ------  shared storage
route 53  ----- private dns service 
IAM , EBS , ACM etc etc

----
Architect : 
[AWS Lift Shift project] 
![image](https://github.com/qriz1452/Imranteli-vprofile-project/assets/112246222/eabb82bd-d512-4ec3-b1af-0b01191e2813)


![image](https://github.com/qriz1452/Imranteli-vprofile-project/assets/112246222/ae5a04ec-7fa2-4d58-abbe-08625e7165a8)


------

create SSL certificate from ACM  and validate with dns provider by adding records.

create 3 SG  : 
1st for ELB -- 80  ,443 port   :  allow 
2nd for tomcat -- 8080 for  app server , ELB   : ALLOW
3rd for backend  -- appserver , ports for services used ,  internal traffic from same SG :  ALLOW  ,,,, application.properties filr in SRC will have port details we can check in that file .


---------


Git branch : AWS-liftandshift


------


laucnh instance and the scripts in user data // scripts that we used in 2nd project for launching  and configuring services mysq;,memcache,tomcat,rabbitmq etc

to check userdata :  `curl http://<ip>/latest/user-data `


login to each vm and confirm each service is installed or not.
to check service is running on a port or not : `ss -tunlp | grep 8080`
or we can do `systemctl`

------


Route53 : 

create private hostedzone
select region and vpc
create record  -> simple routing  -> define simple records
the add all backend vms private ips like this : ( in project 1 and 2 we did this using /etc/hosts file)
![image](https://github.com/qriz1452/Imranteli-vprofile-project/assets/112246222/17adb651-c08a-4579-be8c-11de4e4064de)



------

create IAM user with full acces of s3  and create access keys. we created this user to push artifact/files to s3 from our pc to s3. also as we have full access we can mange s3 as well.

we need the artifact to copy from laptop -> s3  -> tomcat ec2 .,,, the tomcat instance will use artifact for webapp.

attach s3 role to tomcat ec2.
ssh ec2 and cp from s3 to var/lib/tomcat9/webapp folder , make sure to remove ROOT.war and then restart tomcat9

-----

ELB for app server :


create target group , port - 8080 (tomcat) 
health check : /login and override port to 8080

create ELB -> application loadbalancer -> internet facing

add elb cname in DNS record

------

autoscaling :
create image of appserver
create launch configuration
create autoscaling group

--------

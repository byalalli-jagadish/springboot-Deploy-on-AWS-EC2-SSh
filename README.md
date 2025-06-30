"# springboot-Deploy-on-AWS-EC2-SSh" 


1️⃣ Launch EC2 instance

•	OS: Amazon Linux 2023

•	Type: t2.micro (or your choice)

•	Create/download key pair (mykey.pem)

•	Enable Auto-assign public IP

•	Configure security group:

			Allow SSH (port 22) — from your IP / 0.0.0.0/0
			Allow Custom TCP (port 8080) — from 0.0.0.0/0 (for app access)

2️⃣ Connect to EC2 via SSH


		ssh -i /c/Users/LENOVO/Desktop/Learn/mykey.pem ec2-user@3.111.196.244
  
3️⃣ Install Java



		sudo yum update -y
		sudo dnf install java-17-amazon-corretto -y
		java -version


4️⃣ Build your Spring Boot JAR locally


		mvn clean package


5️⃣ Copy JAR to EC2



		scp -i /c/Users/LENOVO/Desktop/Learn/mykey.pem /d/Practice/SpringBootEks/target/springboot-eks.jar ec2-user@3.111.196.244:/home/ec2-user/



6️⃣ Run your app



 	On EC2 instance
	java -jar springboot-eks.jar

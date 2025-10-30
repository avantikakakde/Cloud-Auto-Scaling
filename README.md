

# 🌩️ Cloud Auto Scaling  (AWS EC2 + Load Balancer)

## 📘 Overview
This project demonstrates how to deploy a simple web application on multiple EC2 instances behind an AWS Load Balancer, and configure Auto Scaling so the system automatically adds or removes instances based on CPU utilization.

---

## ⚙️ Setup Steps

### 1️⃣ Web App
A simple HTML file (`html.html`) was created and deployed to `/var/www/html/` on each EC2 instance using Apache.


sudo apt update
sudo apt install apache2 -y
sudo systemctl start apache2
sudo cp html.html /var/www/html/

![](./images/Screenshot%202025-10-30%20131359.png)





### 2️⃣ Load Balancer

An Application Load Balancer (ALB) was created:

Type: HTTP (port 80)

Target Group: EC2 instances running Apache

Health Check Path: /html.html
Output: A public URL 

http://one111-1137726.ap-south-1.elb.amazonaws.com/html.html




![](./images/Screenshot%202025-10-30%20131450.png)


----






![](./images/Screenshot%202025-10-30%20131723.png)




### 3️⃣ Auto Scaling Group

An Auto Scaling Group (ASG) was configured using the same instance template:
Min instances: 1
Desired instances: 2
Max instances: 4
Scaling Policy:
Scale out when CPU > 60%
Scale in when CPU < 20%


![](./images/Screenshot%202025-10-30%20131434.png)

🚀 How Auto Scaling Works

When incoming traffic or CPU usage rises, AWS automatically launches new EC2 instances to handle the load.
As traffic drops, extra instances are terminated, saving cost and maintaining high availability.

### 📝 Short Note

In this project, a simple web app was deployed on multiple EC2 instances and placed behind an AWS Application Load Balancer.
An Auto Scaling Group was configured to automatically add or remove instances based on CPU utilization.
When traffic increases, new instances launch to handle the load; when it decreases, extra instances are terminated.
This ensures high availability, performance, and cost efficiency without manual intervention.







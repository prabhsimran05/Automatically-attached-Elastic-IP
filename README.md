# Automatically-attached-Elastic-IP


Step1- Install Elastic IP service
sudo apt-get update
sudo apt install python3-pip
sudo pip install aws-ec2-assign-elastic-ip






Step2- AWS configurations
Create script-
  cd /home/ubuntu/mysql/
sudo nano scriptRun.sh
( And past )
#!/bin/bash
/usr/local/bin/aws-ec2-assign-elastic-ip --access-key AK00000I7UOCG0000 --secret-key 00000BJQqPWKEBe00000O000 --valid-ips (AWS IAM USER)
52.205.121.102,44.194.195.32
Verify this path-
/home/ubuntu/mysql/scriptRun.sh




Step3- Create services
sudo chmod -R 777 /home/ubuntu/mysql/scriptRun.sh
sudo nano /etc/systemd/system/IP.service
( And past )
[Unit]
Description=My custom startup script
[Service]
ExecStart=/home/ubuntu/mysql/scriptRun.sh start
[Install]
WantedBy=multi-user.target


Step4- Enable services
sudo systemctl daemon-reload
sudo systemctl start IP.service
sudo systemctl enable IP.service
sudo systemctl status IP.service

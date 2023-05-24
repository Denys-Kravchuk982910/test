#Social network for volunteers

#Description
This social network was created to help our volunteers and unite them on the one platform.

Presentation
![chrome_0Z5R5Betcu](https://github.com/Denys-Kravchuk982910/op-kp23-Kravchuk/assets/114987963/0ab54bd1-dc09-4d57-9382-fa366ee5343d)

![chrome_YgeWL5Y9A8](https://github.com/Denys-Kravchuk982910/op-kp23-Kravchuk/assets/114987963/1cb11d40-19f3-4a67-ae20-080e5ff75ab8)

![chrome_S6wQlsydWS](https://github.com/Denys-Kravchuk982910/op-kp23-Kravchuk/assets/114987963/71e1498a-9125-4cf3-9567-be2b8a36ce07)



#Get started
1. Clone the server part: git clone https://github.com/Denys209818/DiplomaWork.git
2. Clone the client part: https://github.com/Denys209818/DiplomaWorkFront.git
3. you should publish these projects using embedded vs functions or just use special commands dotnet publish, npm publish.
4. You should start these projects. Dotnet DiplomaWork.dll; npm start


#For developers
1. To build the project you should use the utilities like dotnet build or npm build(for frontend).
2. To delpoy this project you should upload this project on KVM server which will execute this project.
3. To execute the project on the server you can use special services to automate such process. sudo nano /etc/systemd/system/[project].service and add the next content: 
[Unit]
Description=Example .NET Web API App running on Linux

[Service]
WorkingDirectory=/var/www/helloapp
ExecStart=/usr/bin/dotnet /var/www/helloapp/helloapp.dll
Restart=always
[comment]Restart service after 10 seconds if the dotnet service crashes:
RestartSec=10
KillSignal=SIGINT
SyslogIdentifier=dotnet-example
User=www-data
Environment=ASPNETCORE_ENVIRONMENT=Production
Environment=DOTNET_PRINT_TELEMETRY_MESSAGE=false

[Install]
WantedBy=multi-user.target


---- After that, you will see that your project was executed on the server.
(sudo systemctl status [project].service)


To execute frontend you should add the same file (another title) and input the next text and configure it:
server {
    listen        80;
    server_name   example.com *.example.com;
    location / {
        proxy_pass         http://127.0.0.1:5000;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }
}




 

 Created by Denys Kravchuk, student of KPI.
 Copyrighted 2023
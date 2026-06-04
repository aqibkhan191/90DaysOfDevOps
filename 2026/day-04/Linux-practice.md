#linux commands hand-On
-----------------------------------
**ps aux
ps aux --sort=-%mem | head -6**
<img width="1208" height="284" alt="image" src="https://github.com/user-attachments/assets/398ab4a0-f6be-4faf-b395-590040385bf9" />
<img width="1861" height="552" alt="image" src="https://github.com/user-attachments/assets/d5206f89-99e6-41b3-a85e-88f2c8f87f72" />

<img width="1861" height="552" alt="image" src="https://github.com/user-attachments/assets/07462dda-4db1-4983-a468-f23d93f0017b" />

**pgrep systemd**

<img width="1117" height="537" alt="image" src="https://github.com/user-attachments/assets/1d4bda55-7a6a-489d-9a74-111ea8101877" />


##What is a Service?

A service (also called a daemon) is a program that runs in the background all the time — like a waiter always ready to serve.
Examples:

ssh — lets you connect to the machine remotely
cron — runs scheduled tasks automatically
docker — runs containers

systemd is the manager that starts/stops/monitors all these services.

<img width="1080" height="326" alt="image" src="https://github.com/user-attachments/assets/87c1b51e-9987-43c4-8d1a-733231da2e6b" />

**systemctl status cron**

inspect service in details

<img width="1825" height="623" alt="image" src="https://github.com/user-attachments/assets/227bac39-48c8-4631-b577-de3dea230cc4" />

<img width="1434" height="549" alt="image" src="https://github.com/user-attachments/assets/12a488f7-2c62-487d-92b5-cd08adcab042" />






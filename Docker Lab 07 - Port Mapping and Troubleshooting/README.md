\# Docker Lab 07 - Port Mapping and Troubleshooting



\## Objective



Learn how Docker port mapping works, expose services to the host machine, inspect container networking, and troubleshoot common Docker errors such as port conflicts and container name conflicts.



\---



\## Environment



\- Host: Windows 11

\- Docker Desktop

\- Nginx Container

\- PowerShell



\---



\## Create Nginx Container



```powershell

docker run -d --name web -p 8080:80 nginx

```



Purpose:



\- Create a new Nginx container

\- Map host port 8080 to container port 80



\---



\## Verify Running Container



```powershell

docker ps

```



Purpose:



\- Confirm the container is running

\- Verify port mapping



Expected:



```text

0.0.0.0:8080->80/tcp

```



\---



\## Access Nginx from Browser



Open:



```text

http://localhost:8080

```



Result:



\- Nginx Welcome Page displayed successfully



\---



\## Inspect Container IP Address



```powershell

docker inspect web | findstr IPAddress

```



Result:



```text

172.17.0.2

```



Purpose:



\- View the Docker internal network address



\---



\## View Port Mapping



```powershell

docker port web

```



Result:



```text

80/tcp -> 0.0.0.0:8080

80/tcp -> \[::]:8080

```



Purpose:



\- Verify host-to-container port mapping



\---



\## Port Conflict Troubleshooting



Attempted:



```powershell

docker run -d --name web2 -p 8080:80 nginx

```



Error:



```text

Bind for 0.0.0.0:8080 failed: port is already allocated

```



Cause:



\- Port 8080 was already being used by container web



\---



\## Name Conflict Troubleshooting



Attempted:



```powershell

docker run -d --name web2 -p 9090:80 nginx

```



Error:



```text

The container name "/web2" is already in use

```



Cause:



\- Docker created the container during the first attempt

\- Container name already existed



\---



\## Remove Failed Container



```powershell

docker rm web2

```



Purpose:



\- Delete failed container

\- Free container name for reuse



\---



\## Create Second Container



```powershell

docker run -d --name web2 -p 9090:80 nginx

```



Purpose:



\- Create second Nginx container

\- Map host port 9090 to container port 80



\---



\## Verify Both Containers



```powershell

docker ps

```



Result:



```text

web  -> 8080

web2 -> 9090

```



Purpose:



\- Verify multiple containers can use the same internal port

\- Different host ports prevent conflicts



\---



\## Key Concepts Learned



\### Host Port vs Container Port



Example:



```text

8080:80

```



Meaning:



```text

Host Port      = 8080

Container Port = 80

```



\---



\### Docker Internal Networking



Example:



```text

172.17.0.2

```



Purpose:



\- Internal container communication



\---



\### 0.0.0.0



Meaning:



```text

All network interfaces

```



\---



\### Common Troubleshooting Workflow



1\. Read the error

2\. Identify the problem category

3\. Investigate

4\. Fix

5\. Recreate if necessary



\---



\## Screenshots



\### Nginx Welcome Page



!\[Nginx Welcome](screenshots/01-nginx-browser.png)



\### Container IP Inspection



!\[Container IP](screenshots/02-container-ip.png)



\### Port Conflict Troubleshooting



!\[Troubleshooting](screenshots/03-troubleshooting.png)



\### Multiple Containers Running



!\[Containers Running](screenshots/04-containers\_running.png)



\---



\## Skills Practiced



\- Docker Networking

\- Port Mapping

\- Container Inspection

\- Docker Troubleshooting

\- Nginx Deployment

\- Docker CLI

\- PowerShell


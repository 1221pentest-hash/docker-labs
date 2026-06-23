\# Docker Lab 10 - Docker Networks



\## Objective



Learn how Docker Networks allow containers to communicate with each other using custom bridge networks and Docker DNS resolution.



\---



\## Environment



\* Windows 11

\* Docker Desktop

\* PowerShell

\* Alpine Linux Containers



\---



\## Commands Used



\### List Existing Networks



```powershell

docker network ls

```



\### Create Custom Network



```powershell

docker network create lab10-network

```



\### Create Container 1



```powershell

docker run -dit --name client1 --network lab10-network alpine sh

```



\### Create Container 2



```powershell

docker run -dit --name client2 --network lab10-network alpine sh

```



\### Verify Containers



```powershell

docker ps

```



\### Access Container



```powershell

docker exec -it client1 sh

```



\### Test Connectivity



```sh

ping client2

```



\### Inspect Network



```powershell

docker network inspect lab10-network

```



\### Remove Containers



```powershell

docker rm -f client1 client2

```



\### Remove Network



```powershell

docker network rm lab10-network

```



\---



\## Results



Docker successfully:



\* Created a custom bridge network

\* Connected multiple containers to the network

\* Assigned IP addresses automatically

\* Provided automatic DNS resolution

\* Allowed container-to-container communication



\---



\## Network Topology



```text

client1

&#x20;  │

&#x20;  ▼

lab10-network

&#x20;  ▲

&#x20;  │

client2

```



\---



\## DNS Resolution Test



From inside client1:



```sh

ping client2

```



Result:



```text

PING client2 (172.19.0.3)

```



Docker automatically resolved:



```text

client2

```



to:



```text

172.19.0.3

```



without manually configuring DNS.



\---



\## Network Inspection



Docker network inspection displayed:



```text

client1

172.19.0.2

```



and



```text

client2

172.19.0.3

```



Both containers were attached to the custom bridge network.



\---



\## Concepts Learned



\### Docker Networks



Docker Networks allow containers to communicate securely.



\---



\### Bridge Networks



A bridge network creates an isolated communication environment between containers.



\---



\### DNS Resolution



Docker automatically provides DNS resolution between containers on the same network.



Example:



```text

client1 → client2

```



instead of:



```text

client1 → 172.19.0.3

```



\---



\### Network Inspection



Docker provides detailed network information using:



```powershell

docker network inspect

```



\---



\## Screenshots



\### Existing Networks



!\[Existing Networks](screenshots/01-docker-network-ls.png)



\### Custom Network Created



!\[Custom Network](screenshots/02-custom-network-created.png)



\### Client1 Running



!\[Client1](screenshots/03-client1-running.png)



\### Two Containers Running



!\[Two Containers](screenshots/04-two-containers-running.png)



\### Connectivity Test



!\[Ping Test](screenshots/05-ping-client2.png)



\### Network Inspection



!\[Network Inspect](screenshots/06-network-inspect.png)



\### Cleanup



!\[Network Removed](screenshots/07-network-removed.png)



\---



\## Skills Practiced



\* Docker Networks

\* Bridge Networks

\* DNS Resolution

\* Container Communication

\* Network Inspection

\* Troubleshooting

\* Linux Containers

\* Docker CLI

\* Technical Documentation



\---



\## Key Takeaway



Docker Networks allow containers to communicate using container names instead of IP addresses, simplifying application deployment and service discovery.




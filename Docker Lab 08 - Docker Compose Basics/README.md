\# Docker Lab 08 - Docker Compose Basics



\## Objective



Learn how to use Docker Compose to deploy and manage containers using a YAML configuration file instead of manually creating containers with Docker CLI commands.



\---



\## Environment



\* Windows 11

\* Docker Desktop

\* PowerShell

\* Docker Compose v5.1.4



\---



\## Docker Compose File






## Docker Compose File

### docker-compose.yml

```yaml
services:
  web:
    image: nginx
    ports:
      - "8081:80"



\### Explanation



| Setting      | Description                               |

| ------------ | ----------------------------------------- |

| services     | Defines the containers managed by Compose |

| web          | Service name                              |

| image: nginx | Uses the official Nginx image             |

| ports        | Defines port mapping                      |

| 8081:80      | Host Port 8081 → Container Port 80        |



\---



\## Commands Used



\### Verify Docker Compose



```powershell

docker compose version

```



\---



\### Display Compose File



```powershell

type docker-compose.yml

```



\---



\### Deploy Services



```powershell

docker compose up -d

```



\---



\### Verify Running Containers



```powershell

docker ps

```



\---



\### Stop and Remove Services



```powershell

docker compose down

```



\---



\## Results



Docker Compose successfully:



\* Created a Docker network automatically

\* Created an Nginx container automatically

\* Assigned a project-based container name

\* Published Nginx on port 8081

\* Removed the container and network when the project was stopped



\---



\## Container Information



Generated Container Name:



```text

dockerlab08-dockercomposebasics-web-1

```



Generated Network:



```text

dockerlab08-dockercomposebasics\_default

```



\---



\## Browser Test



URL:



```text

http://localhost:8081

```



Result:



```text

Welcome to nginx!

```



The Nginx web server was successfully accessed through the mapped host port.



\---



\## Concepts Learned



\### Infrastructure as Code



Instead of manually creating containers:



```powershell

docker run -d --name web -p 8080:80 nginx

```



Docker Compose allows infrastructure to be defined in a YAML file and deployed using:



```powershell

docker compose up -d

```



\---



\### Port Mapping



```yaml

ports:

&#x20; - "8081:80"

```



Meaning:



```text

Host Port      = 8081

Container Port = 80

```



Users connect to the Host Port.



\---



\### Automatic Container Naming



Docker Compose automatically generates container names using:



```text

Project-Service-Instance

```



Example:



```text

dockerlab08-dockercomposebasics-web-1

```



\---



\### Automatic Network Creation



Docker Compose automatically creates a dedicated network for the project:



```text

dockerlab08-dockercomposebasics\_default

```



This network is automatically removed when:



```powershell

docker compose down

```



is executed.



\---



\## Screenshots



\### Compose File



!\[Compose File](screenshots/01-compose-file.png)



\### Docker Compose Up



!\[Docker Compose Up](screenshots/02-type\_docker-compose.yml.png)



\### Running Containers



!\[Running Containers](screenshots/03-docker ps.png)



\### Nginx Browser Test



!\[Nginx Browser Test](screenshots/04-nginx-compose-browser.png)



\### Docker Compose Down



!\[Docker Compose Down](screenshots/05-docker\_compose\_down.png)



\### Verification After Removal



!\[Verification After Removal](screenshots/06-DCB\_docker\_ps.png)



\---



\## Troubleshooting Notes



\### Why did Docker Compose create a long container name?



Docker Compose automatically generates names to avoid conflicts between projects.



Example:



```text

dockerlab08-dockercomposebasics-web-1

```



This naming format allows multiple Compose projects to run simultaneously.



\---



\### Why did docker compose down not remove my other containers?



Docker Compose only manages containers defined in the current project's compose file.



Containers created outside the project remain untouched.



Example:



```text

web

web2

```



continued running after:



```powershell

docker compose down

```



\---



\## Skills Practiced



\* Docker Compose

\* YAML Configuration

\* Infrastructure as Code

\* Container Deployment

\* Container Lifecycle Management

\* Docker Networking

\* Port Mapping

\* Nginx Deployment

\* Docker CLI

\* PowerShell

\* Troubleshooting

\* Documentation



\---



\## Key Takeaway



Docker Compose allows infrastructure to be described in a YAML file and managed with simple commands:



```powershell

docker compose up -d

docker compose down

```



This approach is easier to maintain, reproduce, and scale than manually creating containers with individual Docker commands.




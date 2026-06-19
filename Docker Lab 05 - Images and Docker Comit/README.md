\# Docker Lab 05 – Images and Docker Commit



\## Objective



Learn how Docker images and containers work together and how to create a custom Docker image using `docker commit`.



\---



\## Skills Practiced



\* Creating Docker containers

\* Entering containers with Docker Exec

\* Installing software inside a container

\* Understanding the difference between images and containers

\* Creating custom Docker images

\* Verifying image persistence

\* Docker image management



\---



\## Environment



Host OS: Windows 11



Docker Engine: Docker Desktop



Base Image: Ubuntu Latest



Custom Image: ubuntu-nano:v1



\---



\## Command History



\### Display Available Images



```powershell

docker images

```



Purpose:



Display all locally stored Docker images.



\---



\### Create Container



```powershell

docker run -dit --name lab5 ubuntu

```



Purpose:



Create and start a container from the Ubuntu image.



\---



\### Verify Container



```powershell

docker ps

```



Purpose:



Verify the container is running.



\---



\### Enter Container



```powershell

docker exec -it lab5 bash

```



Purpose:



Open an interactive shell inside the container.



\---



\### Verify Identity



```bash

whoami

hostname

pwd

```



Purpose:



Identify user, machine, and current location.



\---



\### Update Package Lists



```bash

apt update

```



Purpose:



Download the latest package information.



\---



\### Install Nano



```bash

apt install nano -y

```



Purpose:



Install the Nano text editor.



\---



\### Verify Nano Installation



```bash

nano --version

```



Purpose:



Confirm Nano is installed successfully.



\---



\### Exit Container



```bash

exit

```



Purpose:



Leave the container shell.



\---



\### Create Custom Image



```powershell

docker commit lab5 ubuntu-nano:v1

```



Purpose:



Create a new Docker image from the modified container.



\---



\### Display Images



```powershell

docker images

```



Purpose:



Verify the new image exists.



\---



\### Remove Original Container



```powershell

docker rm -f lab5

```



Purpose:



Delete the original container.



\---



\### Create New Container From Custom Image



```powershell

docker run -dit --name lab5-test ubuntu-nano:v1

```



Purpose:



Launch a container using the custom image.



\---



\### Verify Persistence



```powershell

docker exec -it lab5-test bash

```



```bash

nano --version

```



Purpose:



Verify Nano is still installed.



\---



\## Image Lifecycle



```text

ubuntu:latest

&#x20;       │

&#x20;       ▼

Create Container (lab5)

&#x20;       │

&#x20;       ▼

Install Nano

&#x20;       │

&#x20;       ▼

docker commit

&#x20;       │

&#x20;       ▼

ubuntu-nano:v1

&#x20;       │

&#x20;       ▼

Create New Container

&#x20;       │

&#x20;       ▼

Nano Already Installed

```



\---



\## Troubleshooting



\### Issue: Container Deleted



Command:



```powershell

docker rm -f lab5

```



Observation:



Container removed successfully.



Lesson:



Changes inside a container are temporary unless committed to a new image.



\---



\### Issue: Understanding Image vs Container



Confusion:



Where is Nano stored?



Resolution:



Nano is stored in the new image created by:



```powershell

docker commit lab5 ubuntu-nano:v1

```



\---



\## Lessons Learned



\* Images are templates.

\* Containers are running instances of images.

\* Changes inside a container are temporary.

\* Docker Commit creates a new image from a container.

\* Custom images can be reused to create multiple containers.

\* Docker images provide consistency and repeatability.



\---



\## Knowledge Check



Question:



After running:



```powershell

docker commit lab5 ubuntu-nano:v1

```



Where is Nano stored?



Answer:



```text

ubuntu-nano:v1

```



The software is now part of the custom image and will exist in future containers created from that image.





\## Screenshots



\### Container Creation



!\[Container Creation](screenshots/LAB5-start.png)



\### Container Verification



!\[Container Verification](screenshots/LAB5-container-whoami.png)



\### Docker Commit



!\[Docker Commit](screenshots/LAB%205%20-COMIT.png)



\### Custom Image Verification



!\[Custom Image Verification](screenshots/LAB5-docker-custom-image.png)




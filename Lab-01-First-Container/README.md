# Docker Lab 01 - First Container Deployment

## Overview

This lab introduces the fundamental concepts of Docker, including images, containers, port mapping, detached mode, and basic troubleshooting.

The goal of this lab was to deploy a web server using Docker and access it through a web browser.

---

## Objectives

* Install and verify Docker
* Run the first Docker container
* Understand the difference between images and containers
* Deploy an Nginx web server
* Learn port mapping
* Practice troubleshooting common Docker errors

---

## Technologies Used

* Docker Desktop
* Nginx
* Windows 11
* PowerShell

---

## Lab Architecture

```text
Browser
    │
localhost:8080
    │
Docker Port Mapping
    │
Container: myweb
    │
Nginx Web Server
    │
Port 80
```

---

## Docker Concepts Learned

### Docker Image

A Docker image is a blueprint or template used to create containers.

Examples:

* nginx
* hello-world

### Docker Container

A container is a running instance of an image.

Example:

```text
Image: nginx

Container: myweb
```

One image can be used to create multiple containers.

---

## Commands Used

### Verify Docker Installation

```powershell
docker --version
```

### Run First Test Container

```powershell
docker run hello-world
```

### Display Downloaded Images

```powershell
docker images
```

### Display All Containers

```powershell
docker ps -a
```

### Run Nginx in Detached Mode

```powershell
docker run -d --name myweb -p 8080:80 nginx
```

### Display Running Containers

```powershell
docker ps
```

---

## Port Mapping Explained

The following option was used:

```powershell
-p 8080:80
```

Meaning:

```text
Host Machine Port 8080
           │
           ▼
Container Port 80
```

This allows a browser to access the Nginx web server running inside the container.

Access URL:

```text
http://localhost:8080
```

---

## Troubleshooting

### Error Encountered

```text
The container name "/myweb" is already in use
```

### Cause

A container named "myweb" already existed on the system.

### Resolution

Removed the existing container and recreated it with the correct configuration.

---

## Results

Successfully deployed an Nginx container and accessed the web application through a browser.

Verified:

* Docker installation
* Container creation
* Image downloads
* Port mapping
* Web server deployment
* Basic Docker troubleshooting

---

## Screenshots

### Docker Installation

![Docker Version](screenshots/01-docker-version.png)
<img width="526" height="71" alt="Capture d’écran 2026-06-07 115519" src="https://github.com/user-attachments/assets/f1db89aa-eb0c-429a-b2ba-754fd129734f" />
<img width="1323" height="581" alt="Capture d’écran 2026-06-07 103533" src="https://github.com/user-attachments/assets/15ca2296-8a73-4e4d-be1c-311a75fb8c81" />

### Hello World Container

![Hello World](screenshots/02-hello-world.png)
<img width="1012" height="493" alt="Capture d’écran 2026-06-07 094103" src="https://github.com/user-attachments/assets/80fe350d-c098-4380-9d54-04596b4a03ba" />

### Docker Images

![Docker Images](screenshots/03-docker-images.png)
<img width="963" height="150" alt="Capture d’écran 2026-06-07 104346" src="https://github.com/user-attachments/assets/10b06abc-11bd-4a3b-b5e1-5349226df09e" />

<img width="1437" height="537" alt="Capture d’écran 2026-06-07 104703" src="https://github.com/user-attachments/assets/5b7c9e82-d105-44df-91a8-737adf3ceb03" />

### Docker Containers

![Docker PS](screenshots/04-docker-ps-a.png)
<img width="936" height="523" alt="Capture d’écran 2026-06-07 105118" src="https://github.com/user-attachments/assets/a1eabed3-7318-4dd9-84bc-5482707b1a97" />

### Running Nginx Container

![Running Container](screenshots/05-running-nginx.png)
<img width="1323" height="581" alt="Capture d’écran 2026-06-07 103533" src="https://github.com/user-attachments/assets/7e3a43fd-6f24-4a78-a08c-dc4c25dd5b25" />

### Nginx Welcome Page

![Nginx Web Page](screenshots/06-nginx-webpage.png)
<img width="1890" height="1031" alt="Capture d’écran 2026-06-07 105445" src="https://github.com/user-attachments/assets/59fdfc09-94f0-49cc-be55-dd326c39d4bb" />

---

## Key Takeaways

* Docker images are blueprints.
* Docker containers are running instances of images.
* Port mapping allows services inside containers to be accessed externally.
* Detached mode allows containers to run in the background.
* Reading error messages is a critical troubleshooting skill.
* Docker simplifies application deployment and portability.

---

## Skills Demonstrated

* Docker Fundamentals
* Container Management
* Image Management
* Port Mapping
* Linux-based Containers
* Troubleshooting
* Web Server Deployment
* Technical Documentation

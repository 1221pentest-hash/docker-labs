# Docker Lab 02 - Entering a Container and Exploring Linux

## Overview

In Lab 01, I learned how to deploy a Docker container and access a web application through a browser.

In this lab, I will enter a running Docker container and explore the Linux environment inside it.

This lab introduces basic Linux administration concepts within Docker containers and demonstrates why Linux knowledge is essential for DevOps engineers.

---

## Objectives

* Access a running Docker container
* Learn how to execute commands inside a container
* Explore the Linux filesystem
* Locate Nginx configuration files
* View running processes
* Understand the relationship between Docker and Linux

---

## Technologies Used

* Docker Desktop
* Nginx
* Linux
* Windows 11
* PowerShell

---

## Lab Architecture

```text
Windows Host
     │
     ▼
Docker Engine
     │
     ▼
Nginx Container
     │
     ▼
Linux Filesystem
```

---

## Why This Lab Matters

Many people learn Docker commands without understanding what happens inside a container.

A Docker container is not magic.

Most containers run Linux-based environments containing:

* Files
* Directories
* Processes
* Configuration files
* Services

Understanding Linux is a critical DevOps skill because Docker containers commonly run Linux applications.

---

## Commands Used

### Verify Running Container

```powershell
docker ps
```

Purpose:

Display all currently running containers.

---

### Enter Container

```powershell
docker exec -it myweb bash
```

Purpose:

Open an interactive Linux shell inside the running Nginx container.

Command Breakdown:

| Option | Meaning          |
| ------ | ---------------- |
| docker | Docker CLI       |
| exec   | Execute command  |
| -i     | Interactive mode |
| -t     | Terminal session |
| myweb  | Container name   |
| bash   | Linux shell      |

---

### Display Current Directory

```bash
pwd
```

Purpose:

Display the current working directory.

---

### List Files

```bash
ls
```

Purpose:

Display files and directories.

---

### List Files with Details

```bash
ls -la
```

Purpose:

Display detailed information including permissions, ownership, hidden files, and file sizes.

---

### Move to Root Directory

```bash
cd /
```

Purpose:

Navigate to the root of the Linux filesystem.

---

### Display Root Directories

```bash
ls
```

Common directories:

| Directory | Purpose                    |
| --------- | -------------------------- |
| /bin      | System commands            |
| /etc      | Configuration files        |
| /home     | User home directories      |
| /usr      | Applications and utilities |
| /var      | Logs and application data  |
| /tmp      | Temporary files            |

---

### Navigate to Nginx Configuration

```bash
cd /etc/nginx
```

Purpose:

Access Nginx configuration files.

---

### Display Nginx Configuration Files

```bash
ls -la
```

Purpose:

View available Nginx configuration files.

---

### View Nginx Configuration

```bash
cat nginx.conf
```

Purpose:

Display the contents of the main Nginx configuration file.

---

### View Running Processes

```bash
ps aux
```

Purpose:

Display running processes inside the container.

---

### Exit Container

```bash
exit
```

Purpose:

Leave the container and return to PowerShell.

---

## Screenshots

### Entering the Container

![Enter Container](screenshots/01-enter-container.png)

### Current Directory

![PWD Command](screenshots/02-pwd-command.png)

### Root Filesystem

![Root Filesystem](screenshots/03-root-filesystem.png)

### Nginx Configuration Directory

![Nginx Directory](screenshots/04-nginx-config-directory.png)

### Nginx Configuration File

![Nginx Config](screenshots/05-nginx-conf.png)

### Running Processes

![Processes](screenshots/06-process-list.png)

---

## What I Learned

During this lab I learned:

* How to access a running container
* How to execute Linux commands inside a container
* How Linux directories are organized
* Where Nginx stores its configuration files
* How to inspect running processes
* Why Linux administration skills are important for Docker and DevOps

---

## Key Takeaways

* Docker containers often run Linux environments.
* Linux commands can be executed directly inside containers.
* Configuration files are commonly stored in the `/etc` directory.
* Running processes can be inspected using Linux tools.
* Docker and Linux skills complement each other and are both essential for DevOps engineers.

---

## Skills Demonstrated

* Docker Container Management
* Linux Navigation
* Linux Filesystem Exploration
* Process Inspection
* Configuration Management
* Technical Documentation
* DevOps Fundamentals

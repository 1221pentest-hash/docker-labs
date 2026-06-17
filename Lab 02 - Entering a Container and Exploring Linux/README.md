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
<img width="927" height="222" alt="entering container" src="https://github.com/user-attachments/assets/26ac2e13-f534-4ba2-8a1c-11d6d6b00edb" />

### Current Directory

![PWD Command](screenshots/02-pwd-command.png)
<img width="432" height="60" alt="pwd-2" src="https://github.com/user-attachments/assets/f4bcf8d6-1878-407c-ac73-621ad2ea69e3" />
<img width="522" height="72" alt="pwd" src="https://github.com/user-attachments/assets/d646f076-a232-4841-becb-30a4d6ac50d6" />

### Root Filesystem

![Root Filesystem](screenshots/03-root-filesystem.png)
<img width="692" height="761" alt="root + ls" src="https://github.com/user-attachments/assets/2175cdce-90e6-4d01-b176-76663c3a647d" />

### Nginx Configuration Directory

![Nginx Directory](screenshots/04-nginx-config-directory.png)

<img width="476" height="170" alt="conf d  directory" src="https://github.com/user-attachments/assets/c909f403-44eb-464d-999b-dc98d01af30e" />
<<img width="601" height="487" alt="nginx html-2" src="https://github.com/user-attachments/assets/1537a7ee-b528-46dc-8ae6-dbe14941649c" />

<img width="900" height="161" alt="04-ls-l-nginx-directory" src="https://github.com/user-attachments/assets/7949516d-ddea-44f1-853b-90abe20fbd23" />

### Nginx Configuration File

![Nginx Config](screenshots/05-nginx-conf.png)
<img width="707" height="540" alt="nginx config" src="https://github.com/user-attachments/assets/90f9966b-6b26-4168-bbde-a30cc2ff5c67" />

### Running Processes

![Processes](screenshots/06-process-list.png)
<img width="601" height="487" alt="nginx html-2" src="https://github.com/user-attachments/assets/5b691ba5-1379-4e8f-bd27-5e12292fd56b" />
<img width="601" height="487" alt="nginx html-2" src="https://github.com/user-attachments/assets/a8f5479b-20b3-4fcd-9f92-f4e2da9f3bc0" />
<img width="425" height="191" alt="troubleshooting commnand" src="https://github.com/user-attachments/assets/47045960-b6fc-4bbe-9e68-a1074effafc2" />
<img width="422" height="142" alt="nginx html" src="https://github.com/user-attachments/assets/b9630738-c79b-4ca1-8ebb-bc3111bdf738" />


---
## Key Lesson Learned

The most important concept learned in this lab was understanding the difference between the Windows host and the Linux container.

Before running any command, I learned to identify my environment by examining the terminal prompt.

Examples:

* `PS C:\Users\...>` indicates I am on the Windows host.
* `root@container:/#` indicates I am inside a Linux Docker container.

This habit helps determine which commands are available and prevents troubleshooting mistakes.

DevOps Rule #1:

1. Look at the prompt.
2. Ask: "Where am I?"
3. Run commands appropriate for that environment.

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


A Docker container is not just an application. It is a lightweight Linux environment with its own filesystem, users, processes, and configuration files.

During this lab I learned to:

* Enter a running container using docker exec
* Read the Linux prompt
* Identify the current user, machine, and location
* Navigate directories with cd
* List files using ls and ls -l
* Read files with cat
* Inspect Nginx configuration files
* Identify the Linux distribution using /etc/os-release
* Locate the Nginx web root
* Understand that the webpage displayed in the browser is generated from the index.html file served by Nginx

Most important rule:

Before running any command, look at the prompt and ask:
"Where am I?"

---

## Skills Demonstrated

* Docker Container Management
* Linux Navigation
* Linux Filesystem Exploration
* Process Inspection
* Configuration Management
* Technical Documentation
* DevOps Fundamentals

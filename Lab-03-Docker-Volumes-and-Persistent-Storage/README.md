

# Docker Lab 03 – Volumes and Persistent Storage

## Objective

Learn how Docker volumes provide persistent storage that survives container deletion.

---

## Skills Practiced

* Creating Docker volumes
* Listing Docker volumes
* Attaching volumes to containers
* Entering containers with Docker Exec
* Linux navigation
* Creating files inside mounted volumes
* Deleting containers
* Verifying data persistence

---

## Environment

Host OS:

* Windows 11

Container Image:

* Ubuntu Latest

Docker Volume:

* mydata

Container Names:

* volume-test
* volume-test-2

---

## Commands Used

### Create Volume

```powershell
docker volume create mydata
```

### Verify Volume

```powershell
docker volume ls
```

### Download Ubuntu Image

```powershell
docker pull ubuntu
```

### Create Container With Volume

```powershell
docker run -dit --name volume-test -v mydata:/data ubuntu
```

### Enter Container

```powershell
docker exec -it volume-test bash
```

### Verify Current Location

```bash
pwd
```

### Navigate To Volume

```bash
cd /data
```

### List Files

```bash
ls -la
```

### Create Test File

```bash
echo "Sensei Ops Lab 03" > lab03.txt
```

### Read File

```bash
cat lab03.txt
```

### Remove Container

```powershell
docker rm -f volume-test
```

### Create New Container Using Same Volume

```powershell
docker run -dit --name volume-test-2 -v mydata:/data ubuntu
```

---

## Results

A file named lab03.txt was created inside the Docker volume.

The original container was deleted.

A new container was created and connected to the same volume.

The file remained available, proving that Docker volumes provide persistent storage independent of containers.

---

## Key Concepts Learned

Image

* Blueprint used to create containers

Container

* Temporary running instance

Volume

* Persistent storage that survives container deletion

Docker Exec

* Allows access to a running container

Persistent Storage

* Data remains available even after containers are destroyed and recreated

---

## Lessons Learned

The most important lesson from this lab is that application containers should be treated as temporary resources.

Business data should be stored in Docker volumes rather than inside the container filesystem.

This allows containers to be recreated without losing important data.

---

## Outcome

Successfully demonstrated Docker persistent storage using volumes and verified that data survives container deletion and recreation.


## Screenshots

### Docker Volume

![Docker Volume](screenshots/01-docker-volume-ls.png)
<img width="966" height="510" alt="01-docker-volume-ls" src="https://github.com/user-attachments/assets/09862399-a371-41e0-b2ff-e2c38b3503eb" />
### Docker Images

![Docker Images](screenshots/02-docker-images.png)
<img width="966" height="510" alt="02-docker-images" src="https://github.com/user-attachments/assets/c38ba8b9-3968-4109-a48b-8f060ef0a466" />


### Container Creation

![Container Creation](screenshots/03-create-container.png)
<img width="977" height="392" alt="03-create-container" src="https://github.com/user-attachments/assets/e17aa904-dd89-4db8-abd3-c55ae883bb07" />


### File Stored In Volume

![File Stored In Volume](screenshots/04-lab03-file.png)
<img width="442" height="110" alt="04  lab03-file" src="https://github.com/user-attachments/assets/5e163c5f-f9e6-4347-b728-42b9a79baf68" />

### File Survived In New Container

![File Survived](screenshots/05-file-survived.png)

<img width="427" height="183" alt="05-file-survived" src="https://github.com/user-attachments/assets/9cb2e9c7-6314-4a22-98ae-58b2b13c898c" />

<img width="1127" height="260" alt="06-create and delete container" src="https://github.com/user-attachments/assets/85adca35-f2e9-48ef-8462-adc235483d15" />


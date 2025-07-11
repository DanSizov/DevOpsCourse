# App deployment:

1. Create a **VM** in **GC Compute Engine**. Make sure **http traffic** is allowed in **Networking**.
2. Create a firewall rule with target tag `notes-app`, add `0.0.0.0/0` to **IPv4 ranges** and allow `3000,5001` ports. Apply this tag in **VM's settings**.
3. Install **Docker** on the **VM** and create a **network**.
4. Pull and run **BE**, **FE**:

````
docker pull dlippo/devopscourse-notes-backend:latest
docker run -d --name notes-backend --network notes-network -p 5001:5000 dlippo/devopscourse-notes-backend:latest

docker pull dlippo/devopscourse-notes-frontend:latest
docker run -d --name notes-frontend --network notes-network -p 3000:80 dlippo/devopscourse-notes-frontend:latest
````

The result should be identical to the images below

![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)

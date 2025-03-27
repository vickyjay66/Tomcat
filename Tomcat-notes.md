# Tomcat by KK FUNDA

## Topics Covered
- Linux
- Git and GitHub
- Shell Scripting
- Maven

## How to Run JAR/WAR/EAR Files?
- **JAR:** `java -jar <filename>`
- **WAR:** Requires Tomcat (Application Server)
- **EAR:** Requires WildFly (Application Server)

---

## Tomcat Server (Application Server)

### Definition
Tomcat (Apache Tomcat) is an open-source web container used to deploy and run Java-based web applications. It was developed by the **Apache Software Foundation (ASF)**.

### Types of Application Servers
1. **Apache Tomcat** → Can deploy only WAR files, not EAR files.
2. **JBoss/WildFly**
   - **JBoss:** Versions 1.x to 7.x
   - **WildFly:** Version 8.x onwards
3. **WebSphere Application Server** → IBM
4. **WebLogic** → Oracle
5. **GlassFish** → Open-source application server

### Why Use Tomcat?
- Most projects now use **Microservices Architecture**.
- Java microservices are often developed using **Spring Boot**, which uses **Tomcat** as the default application server.

### Difference Between Tomcat and JBoss
- **Tomcat** is mainly used for **web applications**.
- **JBoss** supports both **web and enterprise applications**.

---

## Download and Install Tomcat

### Steps to Download Tomcat
1. **Search "Apache Tomcat Download"** on Google.
2. Visit the official website: [Apache Tomcat Download](https://tomcat.apache.org/download-90.cgi)
3. **Switch to the root user and navigate to `/opt/` directory:**
   ```bash
   sudo su -
   cd /opt/
   ```
4. **Install dependencies:**
   ```bash
   yum install unzip tree wget -y
   ```
5. **Download Tomcat:**
   ```bash
   wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.91/bin/apache-tomcat-9.0.91.zip
   ```
6. **Unzip the downloaded file:**
   ```bash
   unzip apache-tomcat-9.0.91.zip
   ```
7. **Navigate to the Tomcat directory:**
   ```bash
   cd apache-tomcat-9.0.91
   ```
8. **View the directory structure:**
   ```bash
   tree
   ```

---

## Tomcat Directory Structure

### 1. **bin** (Startup and Shutdown Scripts)
   - `startup.sh` (Linux/macOS)
   - `startup.bat` (Windows)
   - `shutdown.sh`
   - `shutdown.bat`
   - `catalina.sh start/stop/restart`

### 2. **conf** (Configuration Files)
   - `server.xml`
   - `tomcat-users.xml`

### 3. **lib** (Contains all required JAR files)

### 4. **logs** (Stores log files)
   - `catalina.log`
   - `hostmanager.log`
   - `manager.log`
   - `localhost.log`

### 5. **webapps** (Deployment Directory)
   - Default applications:
     - `ROOT`
     - `manager`
     - `host-manager`
     - `examples`
     - `docs`

### 6. **work** (Stores compiled application-related files)

### 7. **temp** (Stores temporary files)

---

## Start and Stop Tomcat Server

### Steps:
1. Navigate to the `bin` directory:
   ```bash
   cd /opt/apache-tomcat-9.0.91/bin
   ```
2. **Start Tomcat:**
   ```bash
   sh startup.sh
   # OR
   sh catalina.sh start
   ```
3. **Stop Tomcat:**
   ```bash
   sh shutdown.sh
   # OR
   sh catalina.sh stop
HERE WE SHOULD CHANGE PERMISSIONS TO SH FILES
chmod u+x *.sh

### Check if Tomcat is Running:
```bash
sudo yum install lsof
lsof -i :8080
ps -ef | grep -i "tomcat"
```

### Start/Stop Tomcat from Anywhere
```bash
ln -s /opt/apache-tomcat-9.0.91/bin/startup.sh /usr/bin/startTomcat
ln -s /opt/apache-tomcat-9.0.91/bin/shutdown.sh /usr/bin/stopTomcat
```
Now, you can use `startTomcat` and `stopTomcat` from any directory.

---

## Changing Tomcat Port Number

### Steps:
1. Navigate to the `conf` directory:
   ```bash
   cd /opt/apache-tomcat-9.0.91/conf
   ```
2. Open `server.xml`:
   ```bash
   vi server.xml
   ```
3. Change the **Connector port** (default: `8080`) to a new port (e.g., `9090`).
4. Restart Tomcat:
   ```bash
   sh shutdown.sh
   sh startup.sh
   ```

---

## Deploying Applications in Tomcat

### Steps:
1. **Copy the `.war` file to the `webapps` directory:**
   ```bash
   cp /tmp/maven-web-application.war /opt/apache-tomcat-9.0.91/webapps/
   ```
2. **Restart Tomcat:**
   ```bash
   sh shutdown.sh
   sh startup.sh
   ```
3. **Access the application:**
   ```
   http://your-server-ip:9090/maven-web-application
   ```

---

## Web Servers vs Application Servers

| Web Servers                     | Application Servers              |
|---------------------------------|---------------------------------|
| Handle static requests          | Business logic, dynamic content |
| Apache HTTPD, Nginx             | Tomcat, WildFly                 |
| Load balancing                  | Business logic processing       |

---

## Apache HTTPD Server (Web Server)

### Steps to Install and Start Apache HTTPD

1. **Check if the service is running:**
   ```bash
   service httpd.service status
   ```

2. **Install HTTPD:**
   ```bash
   yum install httpd -y
   ```

3. **Start the Server:**
   ```bash
   service httpd start
   ```

**NOTE:** Default port: **80**

- Example URL: `http://65.0.182.70`

4. **Ensure inbound rules allow HTTP traffic.**

5. **Default Paths:**
   - Web root directory: `/var/www/html`
   - Configuration directory: `/etc/httpd/conf`

---

This document is now properly formatted and complete for GitHub. Let me know if you need any modifications! 🚀




TCP ports are numbered from 0 to 65535, and are categorized into well-known (0-1023), registered (1024-49151), and dynamic/private (49152-65535) ports. 
Here's a more detailed breakdown: 
Well-known ports (0-1023):
These ports are reserved for common, widely used services like HTTP (80), HTTPS (443), SMTP (25), and SSH (22).
Registered ports (1024-49151):
These ports are used by applications or services that are less common but still require specific ports to function properly, such as Remote Desktop Protocol (3389).
Dynamic/Private ports (49152-65535):
These ports are used for temporary or short-lived connections and are not assigned to specific services, often used as source ports for outgoing connections.

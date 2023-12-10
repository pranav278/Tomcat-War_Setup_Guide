# Deploy a WAR File to Tomcat | Linux

## Step 1: Creation of VMs in AWS

1. Log in to the AWS Management Console.

   - Open your preferred web browser.

   - Go to the AWS Management Console website [https://console.aws.amazon.com](https://console.aws.amazon.com).

   - Enter your AWS account credentials to log in.

2. Open the EC2 service.

   - Once you are logged in to the AWS Management Console, you will see a search bar at the top. Type "EC2" into the search bar.

   - From the suggested results, click on "EC2" under the "Compute" category. This will open the EC2 service dashboard.

3. Click on "Launch Instance" to begin the instance creation process.

...

## Step 2: Requirements in Frontendvm

### A] Install the latest version of Chrome on Frontend VM.

...

### B] Install Java SE 17:

```bash
# Update package lists
sudo apt update

# Install OpenJDK 17
sudo apt install openjdk-17-jdk

# Add Java to the system PATH
echo 'export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$PATH:$JAVA_HOME/bin' >> ~/.bashrc
source ~/.bashrc
```

...

### C] Install Tomcat 10:

```bash
# Download Tomcat 10
wget https://downloads.apache.org/tomcat/tomcat-10/v10.0.15/bin/apache-tomcat-10.0.15.tar.gz

# Extract the downloaded file
tar -zxvf apache-tomcat-10.0.15.tar.gz

# Move the Tomcat directory to a desired location (e.g., /opt)
sudo mv apache-tomcat-10.0.15 /opt/

# Start Tomcat
/opt/apache-tomcat-10.0.15/bin/startup.sh
```

...

### D] Install MySQL Workbench 8.0.

```bash
sudo apt update
sudo apt install mysql-workbench
```

## Step 3: Requirements in Backendvm

### A] To install MySQL 8 on Linux:

```bash
sudo apt update
sudo apt install mysql-server
sudo mysql_secure_installation
```

...

### B] Once the MySQL database is installed, create a database named “Books”:

```bash
# Log in to MySQL
sudo mysql -u root -p

# Create the database
CREATE DATABASE Books;

# Exit MySQL prompt
exit
```

...

### C] Check for Open TCP Port 3306 with Test-NetConnection for Both VMs:

```bash
# Check port 3306 on the remote server (replace <remote_server_ip> with the actual IP)
nc -zv <remote_server_ip> 3306
```

...

### D] Create a new user in the "books" schema and provide all privileges:

```bash
# Log in to MySQL
sudo mysql -u root -p

# Create a user and grant privileges
CREATE USER 'new_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON Books.* TO 'new_user'@'localhost';
FLUSH PRIVILEGES;

# Exit MySQL prompt
exit
```

...

### E] Connect to the "Books" database from Frontendvm with the new user created.

```bash
# Log in to MySQL from Frontendvm
mysql -u new_user -p -h <backend_vm_ip> Books
```

Replace `<backend_vm_ip>` with the actual IP address of your backend VM.

...

These Linux commands and configurations should help you set up the required environment on Linux VMs, equivalent to the provided Windows instructions. Remember to adapt paths and specific details according to your actual setup.

```


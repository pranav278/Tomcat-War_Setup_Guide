# Deploy a WAR File to Tomcat | Windows 

---

## Step 1: Creation of VMs in AWS

1. Log in to the AWS Management Console.
   
   - Open your preferred web browser.

   - Go to the AWS Management Console website [https://console.aws.amazon.com](https://console.aws.amazon.com).

   - Enter your AWS account credentials to log in. 

2. Open the EC2 service.
   
   - Once you are logged in to the AWS Management Console, you will see a search bar at the top. Type "EC2" into the search bar.

   - From the suggested results, click on "EC2" under the "Compute" category. This will open the EC2 service dashboard.

3. Click on "Launch Instance" to begin the instance creation process.

4. Choose an Amazon Machine Image (AMI) for Windows Server that qualifies for the free tier.

5. Select an instance type that is eligible for the free tier. Make sure the selected instance type falls within the free tier usage limits.

6. Click on "Next: Configure Instance Details".

7. In the "Network" section, select the desired VPC and subnet for your VMs. If you haven't created a VPC and subnet yet, you can do so by going to the VPC service in the AWS Management Console. Make sure both VMs are launched in the same subnet.

8. Click on "Next: Add Storage" to configure the storage options for your instances. You can use the default storage settings or customize them according to your requirements.

9. Proceed to the next steps by clicking "Next" until you reach the "Configure Security Group" step.

10. Example: We have now created 2 VMs with the following names:

   - Frontendvm
   - Backendvm

   ![1](https://github.com/pranav278/WarDeployment/assets/84725860/23dbba6e-9274-4af9-b0ca-875ae6196432)


---   

## Step 2: Requirements in Frontendvm

A] Install the latest version of Chrome on Front-end VM.

B] Install Java SE 17:

   1. Open your preferred web browser.

   2. Go to the official Oracle Java SE Downloads page [https://www.oracle.com/java/technologies/javase-jdk17-downloads.html](https://www.oracle.com/java/technologies/javase-jdk17-downloads.html).

   3. On the page, you will see different options for downloading Java SE 17. Locate the download section for Windows x64.

   4. After Java installation, below Environment variable needs to be set.

   ![2](https://github.com/pranav278/WarDeployment/assets/84725860/6a356070-3728-402d-8123-9e4b8abd4391)

   ![3](https://github.com/pranav278/WarDeployment/assets/84725860/23be1dd5-e32f-4bec-8df2-de635101cf63)



C] Install Tomcat 10:

   - Open your preferred web browser.

   - Go to the Apache Tomcat download page for version 10 [https://tomcat.apache.org/download-10.cgi](https://tomcat.apache.org/download-10.cgi).

   - Locate the Windows 64-bit zip file and click on the link to download it.

   - Once the download is complete, go ahead and install Tomcat.

   ![4](https://github.com/pranav278/WarDeployment/assets/84725860/975ad75c-9555-4f7a-939c-a69e8aae03ba)

   ![5](https://github.com/pranav278/WarDeployment/assets/84725860/2c504ea0-7133-415b-b4aa-d07373464498)

   ## If you want to start, stop, or restart Apache Tomcat using the Windows Services option, follow these steps:

   1. **Open Windows Services:**

   - Press `Win + R` on your keyboard to open the "Run" dialog box.
   
   - Type `services.msc` and press Enter.

   2. **Locate Apache Tomcat:**

   - In the Services window, scroll down to find the service named something like "Apache Tomcat" or "Tomcat".

   3. **Start Tomcat:**

   - Right-click on the Tomcat service and select "Start" from the context menu.

   4. **Stop Tomcat:**

   - Right-click on the Tomcat service and select "Stop" from the context menu.

   5. **Restart Tomcat:**

   - Right-click on the Tomcat service and select "Restart" from the context menu.

   Remember, when you use the Windows Services option to manage Tomcat, it will start Tomcat as a background service. You won't see a command prompt or any console output. To check if Tomcat is running, you can visit `http://localhost:8080` in your web browser. If the Tomcat page loads, it means the server is running.

   Please note that the exact names and labels may vary slightly depending on the version of Tomcat you have installed and your system configuration.

   ![6](https://github.com/pranav278/WarDeployment/assets/84725860/50a44379-4714-4192-9daf-434fbafab58f)


   - Once the Apache Tomcat is installed, we can further configure and deploy our application by placing WAR files in the appropriate directories within the Tomcat installation directory. Please refer to the snapshots.

   - Open your preferred web browser and enter the following URL to access the Tomcat Manager:

     `localhost:8181`

  ## To deploy a `.war` file in Apache Tomcat on a Windows system, follow these steps:

  1. **Stop Tomcat (if it's running):**
   - Ensure Tomcat is not running. You can stop it using the method you prefer (e.g., using the command line or Windows Services).

  2. **Locate the `webapps` Directory:**
   - Navigate to the directory where Tomcat is installed on your system. This is usually `C:\Tomcat` or a similar location.

  3. **Find the `webapps` Folder:**
   - Within the Tomcat directory, you'll find a folder named `webapps`.

   ![7](https://github.com/pranav278/WarDeployment/assets/84725860/ef7eabe7-4164-408b-9207-c4ab558c1155)


  4. **Place the `.war` File:**
   - Copy the `.war` file you want to deploy.

  5. **Paste the `.war` File:**
   - Paste the `.war` file into the `webapps` folder. This is where Tomcat looks for new applications to deploy.

  6. **Start Tomcat:**
   - Start Tomcat using the method you prefer (e.g., using the command line or Windows Services).

  7. **Check Deployment:**
   - Once Tomcat has started, it will automatically deploy the `.war` file. You can verify this by checking the `webapps` directory. If the deployment was successful, you will find a corresponding folder with the same name as the `.war` file.

  8. **Access the Application:**
   - You should now be able to access the application by going to `http://localhost:8080/application_name`, where `application_name` is the name of the `.war` file (minus the `.war` extension).

  Remember to replace `C:\Tomcat` with the actual path where Tomcat is installed on your system.

  If you encounter any issues during deployment, check the Tomcat logs for any error messages that might provide clues about what went wrong.
  
  ![8](https://github.com/pranav278/WarDeployment/assets/84725860/b86ee228-327a-4329-8393-8c3e2faa72ca)

---
D] Install MySQL Workbench 8.0.

## Step 3: Requirements in Backendvm

A] To install MySQL 8 on Windows, follow these steps:

   1. Visit the official MySQL website at [https://dev.mysql.com/downloads/installer/](https://dev.mysql.com/downloads/installer/).

   2. Scroll down to the "MySQL Community Downloads" section.

   3. Under the "MySQL Community Server" category, click the "Download" button for the Windows x64-bit version.

   4. On the next page, click the "No thanks, just start my download" link to begin the download. The installer file will be saved to your computer.

   5. Locate the downloaded installer file and double-click it to launch the MySQL Installer.

   6. In the installer, you will be presented with the setup wizard. Click "Next" to proceed.

   7. Accept the license terms and click "Next".

   8. On the product selection page, choose "MySQL Server" and click "Next".

   9. Select the appropriate installation type based on your needs. The "Developer Default" option is suitable for most cases. Click "Next" to continue.

   10. Review the configuration summary and click "Execute" to begin the installation process.

   11. The installer will download and install the necessary files. It may take a few minutes.

   12. On the configuration page, leave the default settings as they are unless you have specific requirements. Click "Next".

   13. Set a root password for the MySQL server. Make sure to remember this password as you'll need it later. Click "Next".

   14. Optionally, you can configure additional MySQL products or features. Click "Next" to skip this step.

   15. Click "Execute" to apply the configuration changes.

   16. Once the installation is complete, click "Finish" to exit the installer.

B] Once the MYSQL database is installed, create a database named “Books”:

   1. To create a database, you first need to open the Workbench.

   2. Choose the database server you have access to and connect to it.

   3. Locate the Schema section in the sidebar on the left side and right-click the white (blank) area. Click Create Schema. The schema you create is, in fact, a database.

   4. Click the icon for creating a new schema in the Workbench toolbar.

   5. Name the database.

   6. Click Apply.

   7. Create a Table named "book" in the “books” Schema.

   ![9](https://github.com/pranav278/WarDeployment/assets/84725860/2f9b23f3-a3a8-40c9-a43c-7ccca3082fef)


   9. Check for Open TCP Port 3306 with Test-NetConnection for Both VMs:

      You can use the Test-NetConnection cmdlet to check only TCP ports. For example, to check that TCP port 3306 is open on the remote server:

      `Test-NetConnection -ComputerName <ny-msg01> -Port <3306>`

   ![10](https://github.com/pranav278/WarDeployment/assets/84725860/d478b0bd-509d-41de-b15b-828f1d76e07e)


   11. Create a new user in the books schema and provide all privilege
    
   ![11](https://github.com/pranav278/WarDeployment/assets/84725860/4b2a0e5b-2836-4ffa-babd-436cbda01604)


   12. Connect to the books database from Frontendvm with the new user created.

   ![12](https://github.com/pranav278/WarDeployment/assets/84725860/070a33f3-8c8c-45ee-aab3-b916edbb1d55)


   13. Once the connection is established, go to `localhost:8181` and launch books-ui.

   ![13](https://github.com/pranav278/WarDeployment/assets/84725860/19457b29-9a38-42ac-82d4-7eaf3bdf30ad)

## It sounds like you've successfully connected your application to the database. This is a significant milestone in setting up a web application. !!

# Tutorial: How to Set up Remote Access to Your Course Account on ieng6

## **Prerequisites:**
- Windows OS
- Powershell (comes pre-installed with Windows)
- Administrator Privilege
- Your AD password

## **Step 1: Install Visual Studio Code (VSCode)**
1. Download the latest version of [Visual Studio Code](https://code.visualstudio.com/) for Windows
2. Open the downloaded file and follow the installation instructions. When you are finished installing, open VSCode. It should look like the image below.  
[Image](https://ssgadient.github.com/CSE15L/lab-1/InstallingVSCode.html)

## **Step 2: Remotely Connecting**
1. Install OpenSSH client. Go to Settings → Apps → Optional Features. Click on Add a Feature, locate OpenSSH client, and install. There is no need to install OpenSSH server. 
2. Open VSCode Terminal by going to the menu at the top → Terminal → New Terminal. 
3. Login to your course account using the ```ssh <accountname>@ieng6.ucsd.edu``` command. You will be asked a “do you wish to connect?” prompt, to which you should answer “yes”. You will then be prompted with your AD password, which is invisible when entered into the password field. Note that you may need to visit [https://sdacs.ucsd.edu/~icc/index.php](https://sdacs.ucsd.edu/~icc/index.php) to find your account name, as well as reset your password if you are unable to login. 


## **Step 3: Trying Some Commands**
Now that you’ve successfully logged in, let’s test some linux commands:
- `cd <path>` to change directories
- `ls` to list all files in your current directory
- `pwd` to print the full path of your current directory  
- `cp <file> <path>` to copy a file from one directory to another
- `cat <file>` to print out the contents of a file
- `exit` to logoff the server


## **Step 4: Moving Files with ```scp```**
1. One important command to learn is the scp command, which moves files from our host computer to the remote machine. Usage: ```scp <file> <accountname>@ieng6.ucsd.edu:~/```. You will need to enter your password. 
2. Verify that the file was transferred by using ssh to log back into the server. 

## **Step 5: Setting up an SSH Key**
1. Open Powershell as an Administrator
2. Generate ssh keys using ```ssh-keygen```. You will be prompted to save the key, saving it to the default file is fine. Enter your password and confirm it. 
3. Make sure that ssh-agent is running. Run the ```Get-Service ssh-agent | Set-Service -StartupType Automatic``` command to set the ssh-agent to automatic startup, and start ssh-agent with ```Start-Service ssh-agent```. You can verify that it is running with ```Get-Service ssh-agent```. 
4. Add your keys to the ssh-agent using the ```ssh-add $env:USERPROFILE\.ssh\id_rsa``` command. Authorize with password. 
5. Copy the PUBLIC key to the server’s ssh authorized_keys file using the spc command.  
Usage: ```scp C:\Users\<username>\.ssh\id_rsa.pub <accountname>@ieng6.ucsd.edu:~/.ssh/authorized_keys```
6. Verify that you can login without typing a password! 

## **Step 6: Optimize Remote Running**
1. To login: copy and paste in the ```ssh <accountname>@ieng6.ucsd.edu``` command or use the up-arrow key.
2. To compile and run a java file locally → ```javac <file>.java; java <file>;```
3. To compile and run a java file remotely, use

    ```scp <file> <accountname>@ieng6.ucsd.edu:~/<path>```  

    Followed by

    ```ssh <accountname>@ieng6.ucsd.edu javac <file>.java; java <file>;```

4. To minimize keystrokes, use copy/paste from this document when initially inputting the filename, and the up and down arrows to alternate between the two commands. 
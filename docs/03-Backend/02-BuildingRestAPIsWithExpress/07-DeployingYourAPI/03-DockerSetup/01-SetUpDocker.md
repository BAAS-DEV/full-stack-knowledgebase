# Set Up Docker

## Ubuntu Tutorial

Here is a comprehensive overview of how to install Docker and Docker Desktop on Ubuntu:

1. Start by updating the package manager's cache:

```Bash
sudo apt-get update
```

2. Install the necessary packages to allow the package manager to use the repository over HTTPS:

```Bash
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

3. Add the Docker GPG key:

```Bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

4. Add the Docker repository to the package manager's list of sources:
```Bash
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

5. Update the package manager's cache again:
```Bash
sudo apt-get update
```
6. Install Docker:

```Bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

7. Start the docker daemon

```
sudo systemctl start docker
```

8. Add your user to the docker group to allow you to run Docker commands without sudo:

```
sudo usermod -aG docker $USER
```

9. Log out and log back in for the changes to take effect.

That's it! You should now have Docker and Docker Desktop installed on your Ubuntu machine. You can verify the installation by running the following command:

```
docker --version
```
This should print the version of Docker that you have installed.

## MacOS Tutorial

1. Download the Docker Desktop installation package from the Docker website.

2. Double-click the .dmg file to open it.

3. Drag and drop the Docker icon into the Applications folder.

4. Double-click the Docker icon in the Applications folder to start Docker.

5. You may be prompted to allow Docker to run on your system. If so, click "Allow".

6. The Docker dashboard will open in your default web browser.

7. Click the "Sign In" button in the top right corner of the dashboard.

8. If you don't have a Docker account, create one by clicking the "Sign Up" button.

9. Once you are signed in, click the "Get Started" button to begin using Docker.

That's it! You should now have Docker installed on your macOS machine. You can verify the installation by opening a terminal and running the following command:

```
docker --version
```

This should print the version of Docker that you have installed.


## Windows 10/11

1. First, you will need to install the Docker Engine on your Windows machine. You can do this by going to the following link and downloading the Docker Engine - Community installer:
https://docs.docker.com/engine/install/windows/

2. Once the download is complete, double-click on the installer file to begin the installation process.

3. Follow the prompts to complete the installation process. This may include accepting the terms of service and specifying the installation location.

4. Once the installation is complete, open a command prompt and type the following command to verify that Docker has been installed correctly:

```
docker --version
```

If the command returns the version of Docker that you installed, then Docker has been installed successfully.

5. Next, you will need to install Docker Compose. Docker Compose is a tool that is used to define and run multi-container Docker applications. You can download Docker Compose from the following link:

https://docs.docker.com/compose/install/

Follow the prompts to complete the installation process.

6. Once Docker Compose has been installed, you can verify the installation by typing the following command in a command prompt:

```
docker-compose --version
```

If the command returns the version of Docker Compose that you installed, then Docker Compose has been installed successfully.

That's it! You should now have Docker and Docker Compose installed and ready to use on your Windows 10 or Windows 11 machine. 
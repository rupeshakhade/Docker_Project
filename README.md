Project on Building and Deploying a Docker Image for a React-Django Web App on Ubuntu.

Step 1: Connect to an EC2 instance.
Connect to your ec2 instance using it's pem file & public DNS

---->>ssh -i "< pem file > ubuntu@ < public DNS >

![Screenshot (541)-1](https://user-images.githubusercontent.com/20862722/233547308-75cd2eb1-6b9c-4aa9-be1d-14474a6d1135.jpg)

Step 2: Update the package.
Update the package manager by using below command

----->> sudo apt-get update

Step 3: install docker
Install docker using the below command

----->> sudo apt-get install docker.io

Check the docker version and status.

We can check the docker version and status to ensure that it was properly installed or not.

To verify the Docker Version and Docker status use below commands

----->> systemctl status docker

----->> docker --version.

Step 4: Create directory.
We will create one directory and clone the code from github

----->> mkdir projects

Enter the projects folder

----->> cd projects/

Step 5: Clone the repository from Github.
In this step, we clone the code for the Django-React demo app from Github using the “git clone” command. The code will be downloaded and stored in a directory.

-----> git clone https://github.com/rupeshakhade/react_django_demo_app.git

![Screenshot (542)](https://user-images.githubusercontent.com/20862722/233547461-1389f22d-15d0-46d9-ad6f-3035218ebe48.jpg)

Step 6: Check the files and understand the requirements.
After cloning the code, we can check the files in the directory and understand the requirements needed to run the code. The “ls” command can be used to check the files, and we can refer to the README file and manage.py file to understand the code and its dependencies.

· After doing the clone, a directory will be created with a name called react_django_demo_app

· Go to that directory and do ls to check files.

Commands:
----->>cd react_django_demo1_app
----->>ls

![Screenshot (543)](https://user-images.githubusercontent.com/20862722/233547557-5bfef58f-efe4-4544-894e-98ba7590aeea.jpg)

README file — This is the where developer gives steps to run this code.

Here developer has not given much information about the code so we will other files to understand the code.

Manage.py file — Generally this is the file that contains the main things and we have to run this file by seeing the extension (.py) we can say this is Python project and we need to install Python to run is code.

Requirements.txt file — This is file we will get to know all requirements we need to run this code. Here in this project, we need Django also to run it.

Step 7: Create a Dockerfile.
A Dockerfile is a text file that includes the necessary commands for building a Docker image. In this step, we create a Dockerfile using the “vim Dockerfile” command,

----->>vim Dockerfile

and include the necessary commands such as “FROM”, “RUN”, “COPY”, “EXPOSE”, and “CMD”. These commands are used to install packages, create directories, set environment variables, and specify the command to be run when the container is created.

Docker file — It is a text file that has all commands which need to be run for building a given image.

![Screenshot (545)](https://user-images.githubusercontent.com/20862722/233547630-b446bb77-e0f6-43cd-b8f3-8bf7bcc3a654.jpg)

FROM: This command specifies the base image that the new image will be built on top of. The base image can be an official image from the Docker Hub or a custom image from a private repository.

COPY: This command copies files or directories from the host machine to the container.

EXPOSE: This command informs Docker that the container listens on the specified network ports at runtime.

CMD: This command specifies the command that will be run when a container is created from the image.

Step 8: Build a docker image.
After creating the Dockerfile, we can build the Docker image using the “docker build” command. This command builds an image from the Dockerfile and tags it with a name and version.

Docker image — They are executable packages, bundled with application code & dependencies, software packages, etc. for the purpose of creating containers. Docker images can be deployed to any docker environment and the container can be spun up there to run the application.

----->>docker build . -t react-django-app:latest

![Screenshot (547)](https://user-images.githubusercontent.com/20862722/233547721-682f9943-2914-459a-83b6-a193fc7c5d72.jpg)

After building the Docker image, we can check the images using the “docker images” command. This command lists all the images that have been built on the Docker environment.

![Screenshot (550)](https://user-images.githubusercontent.com/20862722/233547793-ae3139bf-e618-4dc0-bb85-71565497b51a.jpg)

Step 9: Create a Docker container.
Once we have built the Docker image, we can create a Docker container using the “docker run” command. This command creates a container from the image and maps the container’s port to the host’s port.

Docker container — Container hold the entire package that is needed to run a application, libraries and system dependencies.

Now using above images we will create a container by using command
----->>docker run -d -p 8001:8001 react-django-app:latest

: -d is daemon mode or detach mode

: -p is port mapping of container port 8001 to instance port 8001

![Screenshot (550)](https://user-images.githubusercontent.com/20862722/233547925-7dbe00e2-f3ef-46a3-81c9-b13f2ef260af.jpg)


We can check the list of Docker containers using the “docker ps” command. This command lists all the running Docker containers.
![Screenshot (551)](https://user-images.githubusercontent.com/20862722/233548065-14cfaf12-2d3d-4c81-9bb9-c74065bf9f75.jpg)

Step 10: Port opening
Open port 8001 in the instance's security inbound rule Check if the application is running.

Before checking the application on a web browser, we need to open port 8001 in the instance’s security inbound rule to allow traffic to flow to the container.

Step 11: Check if the application is running
Finally, we can copy the public IP of the instance to the web browser and check if the application is running. If everything has been set up correctly, the Django-React demo app should be up and running.
![Screenshot (552)](https://user-images.githubusercontent.com/20862722/233548633-232095f9-075f-4d4c-85b0-148639e8064a.jpg)

In summary, setting up a Docker container for a Django-React demo app on Ubuntu involves updating the packet manager, installing Docker, cloning the code from Github, understanding the code and its requirements, creating a Dockerfile, building the Docker image, creating a Docker container, checking the list of Docker containers, opening the required port in the instance’s security inbound rule, and checking if the application is running on a browse.



![500_F_283424830_9sf5qvuEMPw1fvPIM0g3vmKJHpfsgJwf](https://user-images.githubusercontent.com/20862722/233548684-853f56a6-7e0c-4fb8-b611-2731578279ab.jpg)

Happy Learning.😃🤓


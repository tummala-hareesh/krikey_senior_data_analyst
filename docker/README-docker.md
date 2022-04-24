# Docker for Development on Jupyter Notebooks 
- Container is named **jupyter_krikey**.
- Based on `_jupyter/scipy-notebook_` docker image.
- Volumes have been mapped between local and docker container. This means, what ever you do in your local `krikey_sernior_data_analyst` folder will reflect in the container's `/home/jovyan/work/` folder. 
- Assumption: **Docker** and **Docker-Compose** are already installed on your machine.
    - Follow the instructions to [install docker-compose](https://docs.docker.com/compose/install/)
    

## Build a custom Docker Container for Krikey Assignment
Creating custom docker image is similar to creating a working environment using _pipenv_ or _virtualenv_ or _conda_ in Python. Docker additionally gives us the flexibility to work across multiple platforms that are being used by the team. Here, we create a custom container image on top of _scipy_jupyter_ container and install required libraries using __requirements.txt__ file while building the image. This will give us access to the required libraries in any conatinerized environment i.e., access to libraries in jupyter-notebook environment.

- We can further host the custom image on _DockerHub_ for the team to access. But, for security and privacy reasons, we stick to locally creating and working with docker image.  

```
cd krikey_sernior_data_analyst/docker
docker build -t jupyter_krikey . 
docker images
```

### Points to remembers
- _Assumption_: **Docker** and **Docker-compose** is already installed on the local machine.
- There is no need to build the image everytime you want to work on the project 
- Build the image at the very first instance of the project OR if there are additional python or R libraries that you want to install by default in the image. 
- Very first image build will take few minutes to pull required metadata/images and compile. So, Please be patient! 

## Start **jupyter_krikey** container
```
cd krikey_sernior_data_analyst/docker
docker-compose up -d 
```

## Check if the **jupyter_krikey** container is running 
```
docker ps 
```

## Launch **jupyter_krikey** container in browser
- Use this [http://localhost:7777/lab](http://localhost:7777/lab) to lauch **Jupyter Lab** locally. 


## Stop **jupyter_krikey** container
```
cd krikey_sernior_data_analyst/docker
docker-compose down
```
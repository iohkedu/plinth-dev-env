
# Instructions for setting up your development environment with Docker  

The files for setting up the docker environment in VSCode are locatted in the *.devcontainer* folder. The docker images for the cardano-node and the plinth dev. environment get pulled from the following DockerHub locations: 
* [Cardano node](https://hub.docker.com/r/inputoutput/cardano-node)  
* [Plinth environment](https://hub.docker.com/r/robertinoiog/kenya_course)  

In case you do not want to use a Docker integration inside VSCode editor you can use the Docker image directly. The *Dockerfile* and the *docker-compose-plutus.yml* files are located inside the *.devcontainer* folder. 

In any case you will need to install [Docker Desktop](https://docs.docker.com/get-docker/). It is recomended to install and run Docker Desktop on your native OS. If you want to run Docker Desktop inside a Virtual Machine read through [these notes](https://docs.docker.com/desktop/vm-vdi/). 

The following instructions explain how to setup VSCode with Dcoker:
* Download and install VSCode from [here](https://code.visualstudio.com/). 
* You need to start the Docker Desktop application which will start the Docker daemon. 
* Open VSCode, click on the Manage icon in the bottom left corner and choose the Extensions option. 
![alt text](https://github.com/LukaKurnjek/plutus-dev-env/blob/main/images/dokcer-vscode/extensions-button.PNG) 
* A window showing the Extensions Marketplace will appear on the left side of the VS Code UI. In the search box, type *remote development* and then install this extension whicht is is provided by Microsoft. 
![alt text](https://github.com/LukaKurnjek/plutus-dev-env/blob/main/images/dokcer-vscode/remote-development.PNG) 
* After successfully installing the Remote Development extension, you will note that an **Uninstall** button appears in the extension description tab. 
* Close VSCode, clone this repository to your computer, then open VSCode and in the File menu click Open Folder. Select the folder you have cloned with Git. 
* When VS Code opens, the Remote Development extension will detect the Docker container. You'll see a message asking to reopen your project in the container on the bottom right side. Click the **Reopen in Container** button to build the docker container. 
![alt text](https://github.com/LukaKurnjek/plutus-dev-env/blob/main/images/dokcer-vscode/reopen-in-container.PNG) 
* You can click the Starting Dev Container message to view the log. The build may take some time. After a few minutes, you will see a message in the log saying *Start: Run in container*. This message indicates that the dev container is ready. 
![alt text](https://github.com/LukaKurnjek/plutus-dev-env/blob/main/images/dokcer-vscode/console-log.PNG) 
* You can safely close this terminal window by clicking the trash can icon in the upper right corner of the terminal window. Now, open a new terminal window in VS Code by clicking the **Terminal** menu and then **New Terminal**. 

From the new terminal window you can run and build Plinth projects. With the provided instructions you can run a container inside VSCode for any project which repo provides a working *.devcontainer* folder. 

| :information_source:   | The [plutus-tx-template](https://github.com/IntersectMBO/plutus-tx-template/tree/main) repository provides its own *.devcontainer* folder that contains a development environment for Plinth projects.|  
|------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|   
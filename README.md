# Instructions for setting up a Plinth development enviroment 

This repository aims to maintain up-to-date instructions for setting up a Plinth, formerly knows as PlutusTx, development environment. There are three possibilities how to setup the environment:  
* [Using a docker image](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-docker.md), that can be used standalone or integrated with VSCode. 
* [Using Nix](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-nix.md) that provides a shell which contains all dependencies for building Plinth projects. 
* [Using Demeter.run](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-demeter-run.md) online platform that provides up-to-date development environments for Plinth and other Cardano smart contract languages. 

The [plutus-tx-template](https://github.com/IntersectMBO/plutus-tx-template/tree/main) repository references an up-to-date Docker image and Nix shell that both provide a Plinth development environment, that support the latest Plutus version. 

You can use the instructions provided here to install and set-up VSCode with Docker, Nix or Demeter and then use the *plutus-tx-template* repository if you want to have the latest development environment. A note is added at the end of the Docker and Nix instructions on how to use the development environment provided by the *plutus-tx-template* repository. 

The *plutus-tx-template* repository provides an auction demo project. A walkthrough of the code can be found at the official [Plutus user guide](https://plutus.cardano.intersectmbo.org/docs/category/example-an-auction-smart-contract).  

The [cabal tool](https://cabal.readthedocs.io/en/stable/) is used for building and packaging Haskell programs. Before compiling any project you should update the *cabal package index* with the following command, that tells cabal what packages and versions are available for installation: 
```console
cabal update
```

Once you have set up your developement environment and updated the *cabal package index*, you can build and run an example project with the following command from the location where the `cabal.project` and `<project_name>.cabal` files are located: 
```console
cabal run <executable_name>
```

You can find the executable names in the *executable* sections of the `<project_name>.cabal` file. In case there is only one executable name listed you can skip the name and run only `cabal run`. The command first builds the project and then runs the executable file defined in the *executable* sections. 

| :information_source: | In case the project uses Plutus blueprints it will generate a `blueprint.json` file that contains the compiled code of the validators defined in the project. |  
|----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|  

The following commands perform building and runing a project in two steps:
```console
cabal build <executable_name>
cabal exec <executable_name>
```

To start a REPL for a project use: 
```console
cabal repl
```

Some additional information about the **plinth-dev-env** repository: 

| :information_source: | The **plinth-dev-env** repository contains a demo Plinth project and a Docker image that both work with PlutusV2. They are provided in case a devloper wants to test and develop legacy PlutusV2 code. |  
|----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  

# Instructions for setting up a Plinth development enviroment 

This repository aims to maintain up-to-date instructions for setting up a Plinth, formerly knows as PlutusTx, development environment. There are three possibilities how to setup the environment:  
* [Using a docker image](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-docker.md), that can be used standalone or integrated with VSCode. 
* [Using Demeter.run](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-demeter-run.md) online platform that provides up-to-date development environments for Plinth and other Cardano smart contract languages. 
* [Using Nix](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-nix.md) that provides a shell which contains all dependencies for building Plinth projects.  

The [plutus-tx-template](https://github.com/IntersectMBO/plutus-tx-template/tree/main) repository references an up-to-date Docker image and Nix shell that both provide a Plinth development environment, that support the latest Plutus version. 

| :whale:       | The docker image referenced in this repository supports features from the **Vasil hard fork** which lets you compile Plutus V2 scripts. It also includes Deno v1.32, a open-source JavaScript runtime environment. |  
|---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  

You can use the instructions provided here to install and set-up VSCode with Docker, Nix or Demeter and then use the *plutus-tx-template* repository if you want to have the latest development environment. A note is added at the end of the Docker and Nix instructions on how to use the development environment provided by the *plutus-tx-template* repository. 

The *plutus-tx-template* repository provides an auction demo project. A walkthrough of the code can be found at the official [Plutus user guide](https://plutus.cardano.intersectmbo.org/docs/category/example-an-auction-smart-contract).  

| :information_source: | The **plinth-dev-env** repository contains a demo Plinth project with a PlutusV2 validator that always passes. |  
|----------------------|:---------------------------------------------------------------------------------------------------------------|  

Once you have set up your developement environment you can build the example project with the following commands from the location where the `cabal.project` file is located, which for the *plutus-tx-template* repository is the top location of the repo: 
```console
cabal update
cabal run
```

The `cabal run` command first builds the project and then runs the executable. It will generate a `blueprint.json` file that contains the compiled code of the 
validators defined in the project. 

To only build a project without running it you can run the following command from the location where your `cabal.project` file is located:
```console
cabal build all
```

To start a REPL `cd` into the folder that contains your `<project_name>.cabal` file and run: 
```console
cabal repl
```

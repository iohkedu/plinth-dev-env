# Instructions for setting up a Plutus development enviroment 

This repository aims to maintain up-to-date instructions for setting up a Plutus development environment. There are three possibilities how to setup the environment:  
* [Using a docker image](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-docker.md), that can be used standalone or integrated with VSCode. 
* [Using Demeter.run](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-demeter-run.md) platform that provides an up-to-date online development environment. 
* [Using Nix](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-nix.md) that provides a shell which contains all dependencies for building Plutus projects.  

| :whale:       | The docker image currently supports features from the **Vasil hard fork**.|  
|---------------|:--------------------------------------------------------------------------|  

An example Plutus project is added to this repository. Once you have set up your developement environment you can build the example project with the following commands from the top location of this repository: 
```console
cabal update
cabal build all
```

You can then cd into the *onchain/* fodler and start the REPL with `cabal repl`. 


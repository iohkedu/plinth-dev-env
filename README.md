# Instructions for setting up a Plinth development enviroment 

This repository aims to maintain up-to-date instructions for setting up a Plinth, formerly knows as PlutusTx, development environment. There are three possibilities how to setup the environment:  
* [Using a docker image](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-docker.md), that can be used standalone or integrated with VSCode. 
* [Using Demeter.run](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-demeter-run.md) online platform that provides up-to-date development environments for Plinth and other Cardano smart contract languages. 
* [Using Nix](https://github.com/iohkedu/plutus-dev-env/blob/main/instructions/using-nix.md) that provides a shell which contains all dependencies for building Plinth projects.  

| :whale:       | The docker image referenced in this repository supports features from the **Vasil hard fork** which lets you compile Plutus V2 scripts. It also includes Deno v1.32, a open-source JavaScript runtime environment. |  
|---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  

An example Plinth project is added to this repository. Once you have set up your developement environment you can build the example project with the following commands from the top location of this repository: 
```console
cabal update
cabal build all
```

You can then cd into the *onchain/* fodler and start the REPL with `cabal repl`. 

The [plutus-tx-template](https://github.com/IntersectMBO/plutus-tx-template/tree/main) repository also references a Docker image and it contains a Nix shell that both provide a Plinth development environment, 
which might be more up-to-date then this repository. Nevertheless, you can use instructions provided here to install and set-up VSCode with Docker, Nix or Demeter and then use the provided *plutus-tx-template* 
repository for your development environment. A note is added at the end of the Docker and Nix instructions on how to use the development environment provided by the *plutus-tx-template* repository. 

The *plutus-tx-template* repository also provides an auction demo project. A walkthrough of the code can be found at the official [Plutus user guide](https://plutus.cardano.intersectmbo.org/docs/simple-example/plutus-tx-code/).  


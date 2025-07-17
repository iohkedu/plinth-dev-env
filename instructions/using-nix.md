
# Instructions for setting up your development environment with Nix 

| :information_source: | In case you are a windows user first follow the *WSL installation* instructions that are provided at the bottom of this page. |  
|----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|   

To install *nix* on your system follow the instructions for Linux, Mac OS or Windows (WSL2) that can be found at the [official webpage](https://nixos.org/download). If you are using Linux you might need to disable SELinux ([Fedora instructions](https://docs.fedoraproject.org/en-US/quick-docs/selinux-changing-states-and-modes/#_disabling_selinux)) to be able to install Nix. 

When installing Nix from the command line you will be asked following questions:
```console
Would you like to see a more detailed list of what I will do?
[y/n] n 

Can I use sudo?
[y/n] y 

Ready to continue?
[y/n] 

[sudo] password for user:

Nix won't work in active shell sessions until you restart them.
Press enter/return to acknowledge.
```

After installing Nix, you’ll have to activate flakes and enabele realising store objects during evaluation. You can do this by adding the following line to your nix system configuration file:
```console
experimental-features = nix-command flakes
accept-flake-config = true 
allow-import-from-derivation = true
```

In case you are using Linux you can do that by running the command below which adds the following configuration to the */etc/nix/nix.conf* file:  
```console
cat <<EOF | sudo tee -a /etc/nix/nix.conf
experimental-features = nix-command flakes
accept-flake-config = true 
allow-import-from-derivation = true
EOF
```

To improve build speed, it is possible to set up a binary cache maintained by IOG. This step is optional and can be done by adding the following lines to your nix system configuration file: 
```console
substituters = https://cache.nixos.org https://cache.iog.io
trusted-public-keys = hydra.iohk.io:f/Ea+s+dFdN+3Y/G+FDgSq+a5NEWhJGzdjvKNGv0/EQ= cache.nixos.org-1:6NCHdD59X431o0gWypbMrAURkbJ16ZPMQFGspcDShjY=
```

| :information_source: | The *substituters* and *trusted-public-keys* provided in this repository might change, which does not happen frequently. For latest data check the nix setup instruction at the [plinth-template](https://github.com/IntersectMBO/plinth-template/tree/main) repository. | 
|----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| 


In case you are using Linux you can do that by running the following command: 
```console
cat <<EOF | sudo tee -a /etc/nix/nix.conf
substituters = https://cache.nixos.org https://cache.iog.io
trusted-public-keys = hydra.iohk.io:f/Ea+s+dFdN+3Y/G+FDgSq+a5NEWhJGzdjvKNGv0/EQ= cache.nixos.org-1:6NCHdD59X431o0gWypbMrAURkbJ16ZPMQFGspcDShjY=
EOF
```

Make sure your $USER is trusted. You can check this by running the command `nix show-config | grep trusted-users`.<br>
If it is not add the following line to your nix system configuration file and restart the nix-daemon: 
```console
trusted-users = root <YOUR_USER_NAME>
```

If your Linux OS is systemd-based (see Adoption section at [Systemd](https://en.wikipedia.org/wiki/Systemd) wiki page) you can restart and check the status of the nix-daemon with the following command. 
```console
systemctl restart nix-daemon
systemctl status nix-daemon
```

For instructions on how to run a nix shell that contains the development environment for Plinth, you can either:  
* clone [plinth-template](https://github.com/IntersectMBO/plinth-template/tree/main) repository and run inside the repository:
```console
nix develop
```
| :hourglass:   | When you will run your nix shell for the first time it may take a while until everything has build.|  
|---------------|:---------------------------------------------------------------------------------------------------| 
* or look at IOG's [Developer Experience Shell](https://github.com/input-output-hk/devx) repository for set-up instructions.

| :information_source:   | Once your nix shell has build you can `cd` into your Plinth project directory and start building the project.|  
|------------------------|:-------------------------------------------------------------------------------------------------------------| 

| :information_source:   | The *Developer Experience Shell* lets a user pick from a list of various nix shells that support different GHC versions.|  
|------------------------|:------------------------------------------------------------------------------------------------------------------------|  

## WSL installation 

WSL (Windows Subsystem for Linux) version 2 needs to be installed on your device before installing Nix. WSL 2 is only available in Windows 11 or Windows 10, Version 1903, Build 18362 or later. 

Up-to-date WSL installation instructions can be found at the [official documentation](https://learn.microsoft.com/en-us/windows/wsl/install). At the time of writing the Ubuntu OS gets installed as the default Linux OS. You have the option to chose another distribution from the online store. 

| :information_source: | The installation of a Linux OS through WSL make take a while. |  
|----------------------|:--------------------------------------------------------------|   

If you want to access the file system in your WSL you can execute the following command that will open the currecnt location in your windows explorer: 
```console
explorer.exe .
```

Once WSL2 with a OS is installed on your device you can follow the installation instruction for Nix provided at the begining of this page. 

**WSL VSCode integration**

The [VSCode editor](https://code.visualstudio.com/) provides an integration for WSL. You need to add the `WSL` VSCode extension. Then you can open a folder in your WSL Linux with VSCode by `cd` into it and running `code .`. If you then open a terminal in VSCode (View -> Terminal) it will let you access your WSL. 

If you open the folder with VSCode in windows through explorer, VSCode will promt a message if you want to reopen the folder in WSL. 

![alt text](https://github.com/iohkedu/plinth-dev-env/blob/main/images/nix/VSCode_with_wsl.png)

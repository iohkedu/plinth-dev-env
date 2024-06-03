
# Instructions for setting up your development environment with Nix 

First you will need to install *nix* on your system. Instructions for Linux, Mac OS, Windows (WSL2) and Docker can be found at the [official webpage](https://nixos.org/download). 

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

If your OS is systemd-based you can restart and check the status of the nix-daemon with the following command. 
```console
systemctl restart nix-daemon
systemctl status nix-daemon
```

For instructions on how to run a nix shell that contains the development environment for Plutus, please look at IOG's [Developer Experience Shell](https://github.com/input-output-hk/devx) repository. 

| :hourglass:   | When you will run your Nix shell for the first time it may take a while until everything has build.|  
|---------------|:---------------------------------------------------------------------------------------------------|  


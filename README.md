# Setup a minecraft vanilla server in different versions
Date: 13.11.2021


## Explanation
This is an ansible playbook for dynamic setups/installations of minecraft vanilla servers.
The whole playbook is splitted in 4 roles which are:
* checks
* preparations
* setup
* mc_service

The most impotant tasks can find the setup and mc_service roles.
Every version is supported. This playbook will search for the newest version automatically if you choose the "latest" string as version in the varsfile.
The default values are defined in the default_vars_files directory. If you want to configure the variables by your own,
make a copy of the default varsfile and ad the path to the extra variables.

### What is this playbook doing exactly?
This playbook starts with some checks and setting some variables. 
It installs the required packages and will automatically check for the latest version if selected.
Now it will search for the download url to download the minecraft server file.
A system user will be added on the system and some dependencies follow.
Some Templates will be transfered to the target host and it maces the server ready for the initial start.
After the installation it setup a minecraft service and starts it.
After the whole workflow you can start or stop the service.



## Configuration

### The default variables
The default variables are placed in default_vars_files/default_mc_vars.yml
You can copy and customize a varsfile by yourself and overwrite the path to the variables by using the extra variables parameter "varsfile" at the execusion.
The most variables are easy to understand by the comments. 



## Execution
You need to evaluate you own executions. It depends on the way how you connect to the server. In the following examples the authentification is with user-password and setting the password for the sudo command

### Example execution with the default configuration
```
$ ansible-playbook -i hostname.domain, setup_mc_vanilla_server.yml -e host=all -u remote_username -k -K
```

### Example execution with custom configuration files
```
$ ansible-playbook -i hostname.domain, setup_mc_vanilla_server.yml -e host=all -e varsfile=path/to/customvarsfile.yml -u remote_username -k -K
```


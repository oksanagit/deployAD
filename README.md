# What script does and supports 
This Ansible utility automates deployment of EPICS base and EPICS modules. It targets deployments of areaDetector. Currently it supports:  
- ADSimDetector
- ADProsilica
- ADPointGrey
- ADEiger
- xspress3
group_vars/all.yml defines all configuration details, like which versions to pick and which modules to compile.
host_vars/hostname.yml can redefine (overwrite) any configuration in all.yml.

Script installs needed packages after autodetection of the Operating System on the target host. Debian and RedHat(CentOS) kinds are suppored.

# How to use
To enjoy automation, one needs to have Ansible installed on the master deployment host and have ssh connections to the target hosts. 
Ansible technology supports "parallel"/simultaneous deployments on multiple targets. 
   
The following command will clone and build all supported modules on hosts tagged as ISS in 'hosts' file with the configuration defined in all.yml. 
If --limit is not spesified, script will deploy on *all* hosts spesified in 'hosts' file. 
    
```ansible-playbook -i ./hosts -K deploy.yml --limit=ISS```   
-k requires user login  
-K requires sudo password
   
The following command will clone and build all supported modules on hosts tagged as SRX  as xspress3 user on the target host. 
One will be offered to enter ssh and sudo passwords for 'xspress3' user.    
   
```ansible-playbook -i ./hosts -Kk doDeployment.yml --limit SRX --user xspress3```   



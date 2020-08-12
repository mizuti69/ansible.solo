# Playbook linux_basic
This playbook configures yum and modernizes the OS  

## Tasks overview

### Yum cache enable
enable yum keepcache  

### Add package
Install additional packages  
By default add the following packages  

* yum-utils
* vim
* bind-utils
* git
* net-tools
* epel-release

### Disable repos
Disable epel repositories installed by package addition by default  
If epel is not specified in the package addition, an error will occur.  
Since this process uses the shell module, it will always be chaged at runtime.  

### Upgrade all
Run update all if `yum_update` variable is `yes`  
Default is yes  

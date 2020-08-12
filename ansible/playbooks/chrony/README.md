# Playbook chrony
This playbook makes basic settings for chrony  
The target os is centos or redhatos  

## Tasks overview

### Install chrony
Install chrony if not installed  

### System ntp enabled
enable systemd ntp  
Since this process uses the shell module, it will always be chaged at runtime.  

### Chrony configure
Deploy chrony configuration file from template  
By default, the NTP server referred to by config is as follows  

* servers
    * ntp.jst.mfeed.ad.jp
    * ntp.nict.jp
* pools
    * 0.jp.pool.ntp.org
    * 1.jp.pool.ntp.org
    * 2.jp.pool.ntp.org
    * 3.jp.pool.ntp.org

By default this playbook configures client mode  

> Notice: Setting in server mode is not yet implemented  

```
chrony_mode: client
```

After the deployment is completed, restart the service  

### Chrony enabled
Enable automatic startup  

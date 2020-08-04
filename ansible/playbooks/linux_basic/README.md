# Playbook linux_basic
A playbook with basic settings for RedhatELOS7 or CentOS7

Notice: You need to restart the remote server the first time you run the playbook  

## Tasks overvew

### Confirmation of request package
Identify and install the packages needed to run the playbook  
By default, the following packages are the minimum required  

* libselinux-python
* NetworkManager-glib
* glibc-langpack-ja

### SELinux setting
SELinux contorol parameter settings  
The parameters that can be set are as follows  

* enforcing: SELinux security policy is enforced.
* permissive: SELinux prints warnings instead of enforcing.
* disabled: No SELinux policy is loaded.

### Locale setting
Set locale to `ja_JP.utf8`  
Since this process uses the command module, it will always be chaged at runtime.  

### Localtime setting
Set time zone to `Asia/Tokyo`  

### Hostname setting
Setting the host name  
By default, the host name is referenced by the global variable `ansible_hostname` and is not changed  
If you want to change the host name with a variable, define it in `host_vars`

```
linux_hostname: "{{ ansible_hostname }}"
```

### Sysctl setting
Additional sysctl settings  
By default, the following settings are added and reflected in `sysctl.d/99-custom.conf`  

```
net.ipv4.conf.all.accept_source_route=0
net.ipv4.conf.default.rp_filter=1
net.ipv4.tcp_syncookies=1
net.ipv4.icmp_echo_ignore_broadcasts=1
```

### Systemd log level setting
Change systemd log level to `notice`
Since this process uses the lineinfile module, it will always be chaged at runtime.  

### Disable service
Specifies the service to disable autostart  
The services specified by default are as follows  

* acpid  

# Playvook cron
Playbook to change os job management from anacron to cron  

## Task overview

### Enable cron job
Change the system periodic job to run by cron  
By default it runs at the following times  

```
05 0 * * * root run-parts /etc/cron.daily
25 0 * * 0 root run-parts /etc/cron.weekly
45 0 1 * * root run-parts /etc/cron.monthly
```

### Disable anacron job
Change management time of anacron job management  

```
START_HOURS_RANGE=5-6
```

### Change notification destination of job mail
Change the job notification address for cron and anacron  
Default is `root`

### Add system job for anacron
Add anacron job with changes to cron job management  

* 0anacron.daily
* 0anacron.weeekly
* 0anacron.monthly

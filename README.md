#README

##This is a module that will send API calls to Zendesk in order to do cool stuff.


### Setting up the `drush.inc` file

This function needs to be included in the zendesk_events.module page

```
function drush_zendesk_events_zd_command()
{
    // Put in here the master function you want drush to run.

}
```

This is where the master function should live in the `.module` file. When you call  `drush zd-command`  the PHP code  will run in this function.

** Why is the function named `drush_zendesk_events_zd_command` **

* `drush` is important as this is how drush know what command to run
* `zendesk_events` - this is the name of the module
* `zd_command` is the matching name of the command that can be found when you want to run drush. (i.e. `drush zd_command`)

---
** Running Cron for this module **
This is the cron job that will run on the site when the module is ready:

```
drush @caltestzdmodule.dev zd-command 2>&1 | awk '{print "["strftime("\%Y-\%m-\%d \%H:\%M:\%S \%Z")"] "$0}' &>> /var/log/sites/${AH_SITE_NAME}/logs/$(hostname -s)/drush-zd.log
```

This is the command: `drush @caltestzdmodule.dev zd-command`. It is the only part you actually need for the module and drush to work.


This second part is for logging and error catching on the cron/drush side.

```
2>&1 | awk '{print "["strftime("\%Y-\%m-\%d \%H:\%M:\%S \%Z")"] "$0}' &>> /var/log/sites/${AH_SITE_NAME}/logs/$(hostname -s)/drush-zd.log
```

If you run into an issue, check `/var/log/sites/{SITE_NAME}/logs/{hostname}/drush-zd.log` for the log file.

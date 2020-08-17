# check_mk_cawa
check_mk plugin witch collects [CA Workload Automation](https://en.wikipedia.org/wiki/CA_Workload_Automation_AE) application(s) progress and alert on status trouble.


# Dependencies:
This script uses ``/opt/CA/WorkloadAutomation/bin/cli`` binary to query CA Workload Automation the status of an application. It's path should be setted as parameter.

# How to setup:
This plugin should be placed in ``/usr/lib/check_mk_agent/local/60/``, so this check works async with check_mk_agent avoiding timeouts if it last. The name of the folder (60) indicates frecuency in seconds in witch plugin would be executed. Name this folder as you need. More apps you check, longer time expend on checking. If command execution fails, CRIT incident will be reported.

Custom apps to check. You can check available apps with command:
```
sh /opt/CA/WorkloadAutomation/bin/cli hostname puerto usuario password 'listevent' | grep "Application name" | awk '{print $3}'`)
```

Give it execution permissions:
```
chmod +x check_mk_cawa
```
You cant check if plugin works:
![Chequeo del plugin](https://github.com/martinmartossimon/check_mk_cawa/blob/master/images/check_output.png)

After doing discovery, you could check the services:
![Servicios]()
![Graficas]()

## Monitor CPU and Memory as Windows metrics

### Create new dashboard
1. Add 'problem' widget (configurating for testing purpose)
- Refresh interval:30s 
- Host:windows
- Severity:all selected
- Acknowledgement status:Acknowledged

2. Add 'Graph' widget for CPU metrics
- Refresh interval:30s
- Host patterns:windows
- Item patterns: 
1. CPU interrupt time:
Time CPU spends handling hardware interrupts.
High interrupt time can indicate hardware or driver problems.
2. CPU privileged time: 
Time CPU spends in kernel mode, executing system calls.
High values may indicate OS-level activity (drivers, I/O).
3. CPU Queue Length:
Number of threads waiting for CPU.
Useful for spotting CPU bottlenecks.
4. CPU User Time:
Time CPU spends running user-mode processes (applications, not OS kernel).
If high constantly, some program might be using too much CPU.
5. CPU DPC time:
Deferred Procedure Call and useful for detecting driver problems.


### Triggers set on 1 minute

- On Data Collection -> Templates -> Windows by Zabbix Agent -> Triggers -> Click on each Trigger name and set expression for 1m instead of default 5m.
- Modify severity 


### Stress test to evaluate how Zabbix records and visualizes system metric changes


.


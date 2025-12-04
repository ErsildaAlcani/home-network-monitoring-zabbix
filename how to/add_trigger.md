## Add trigger

### What is a trigger and why is it important?

Triggers are what allow Zabbix to decide when to fire an alert.A logical expression evaluates the data collected by items and determines whether a certain condition indicates a problem.

### What trigger is required for testing purposes?

Configure a trigger to generate a High-severity event when CPU usage on a windows host exceeds 60% for a continuous period of 1 minutes.


### How to?

 1. On Data Collection -> Templates -> Windows by Zabbix Agent -> Triggers -> Add Trigger.
 2. Set name.
 3. Choose Severity according to operation rules.
 4. Add expression. A Condition window will open
    - Choose the item to monitor. In this case Windows by Zabbix agent: CPU utilization
    - Function avg() - Maximum value for period T
    - Last of (T): 1 Time
    - Time shift: null
    - Result: >60
 5. PROBLEM event generation mode: multiple. So the event will be triggered until fixed.
 6. Add description: 'CPU utilization is above 60%. Intervention needed.'

 ### Expression created

 > avg(/windows/perf_counter_en["\Processor Information(_total)\% User Time"],2)>60


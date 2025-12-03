# All the steps to add on Zabbix a kali linux (vm) host
>the following steps are followed in the video attached to the project
## Add host on Zabbix
1. Navigate to the Hosts Page
   In the left menu, go to: Data Collection → Hosts
   There will be a list of all existing hosts.
---
2. Create a New Host
Click the “Create host” button in the top right corner.
---
3.  Fill in Host Details


##### Host name: linux.
##### Groups: Linux servers & personal usage (a new group already created).
##### Interfaces:

---

- Click Add under “Agent interfaces”.
- Enter the IP address of the host: 192.169.0.109
- Select the correct port (default: 10050 for agent).
- DNS name: Leave blank if you are using IP.
---
4. Link Templates
Templates define what Zabbix monitors on the host.
Go to the Templates tab → click Select → choose relevant template(s):Linux by Zabbiagent
Click Add to link the template.
---
5. Save the Host
Click Add at the bottom of the page.
The host will now appear in the list.
Zabbix will start monitoring it according to the linked template(s).

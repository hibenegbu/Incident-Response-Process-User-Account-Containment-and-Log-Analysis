# Incident-Response-Process-User-Account-Containment-and-Log-Analysis

# Incident Response: User Account Containment and Log Analysis

This project demonstrates **my Incident Response Process**, conducted on a Kali Linux system, where I detected and neutralized a compromised user account (`malicious_user`). Below is a step-by-step breakdown of the process and screenshots showing my actions.

## Table of Contents
1. [Introduction](#introduction)
2. [Step 1: Identifying Suspicious Activity] (#step-1-identifying-suspicious-activity)
3. [Step 2: Containing the Compromised User Account] (#step-2-containing-the-compromised-user-account)
4. [Step 3: Investigating Running Processes] (#step-3-investigating-running-processes)
5. [Step 4: Reviewing Network Connections] (#step-4-reviewing-network-connections)
6. [Step 5: Reviewing Logs for Further Suspicious Activity] (#step-5-reviewing-logs-for-further-suspicious-activity)
7. [Step 6: Verifying and Restarting Logging Services] (#step-6-verifying-and-restarting-logging-services)
8. [Step 7: Final Cleanup and User Deletion] (#step-7-final-cleanup-and-user-deletion)
9. [Conclusion](#conclusion)
## Introduction
In this project, I performed an incident response process on a compromised account on a Kali Linux system. My steps included identifying suspicious activity, containing the issue, investigating processes, reviewing logs, and verifying system integrity.

## Step 1: Identifying Suspicious Activity
System logs showing failed login attempts and sudo command failures were the first indication of a compromise. I used the following commands to investigate:
- **Checking for failed login attempts:**
-s **udo grep 'Failed' /var/log/auth.log
-	**Checking sudo command attempts for unusual activity:
- **sudo grep 'sudo' /var/log/auth.log
-	**Viewing system activity logs:
sudo tail -n 100 /var/log/syslog
## Step 2: Containing the Compromised User Account
Once I confirmed the suspicious activity, I immediately locked the malicious_user account to prevent further login attempts:
-	**Locking the user account:
- **Sudo usermod -L malicious_user
-	**Confirming the account was disabled:
- **su malicious_user
## Step 3: Investigating Running Processes
I identified and terminated any active processes associated with malicious_user:
-	**Listing active processes:
- **ps aux | grep malicious_user
-	**Killing any suspicious processes:
- **sudo kill <process_id>
## Step 4: Reviewing Network Connections
I checked if the compromised user had established any suspicious network connections:
-	**Listing active network connections and services:
- **sudo netstat -tulnp
Step 5: Reviewing Logs for Further Suspicious Activity
I reviewed the system logs for any additional suspicious activities after the user account was locked:
-	**Checking for failed login attempts:
- **sudo grep 'Failed' /var/log/auth.log
-	**Reviewing sudo activities:
- **sudo grep 'sudo' /var/log/auth.log
## Step 6: Verifying and Restarting Logging Services
To ensure the logging services were working correctly, I checked and restarted the rsyslog service:
-	**Checking the status of rsyslog service:
- **sudo service rsyslog status
-	**Restarting rsyslog if needed:
-**sudo systemctl restart rsyslog
## Step 7: Final Cleanup and User Deletion
After confirming that the system was clean and secure, I deleted the malicious_user account:
-	**Deleting the user account:
-**sudo userdel malicious_user
-	**Verifying the user account was removed:
- **cat /etc/passwd | grep malicious_user

- **Conclusion
I completed the incident response process, securing the system by disabling and removing the compromised account. My logs confirmed no further suspicious activity. This project demonstrates the critical steps I took in analyzing and securing the compromised system, including log analysis, process termination, and network monitoring.
 
Tools I Used:
•	Kali Linux
•	Wireshark
•	netstat
•	rsyslog

![image](https://github.com/user-attachments/assets/41669b64-0e39-4c24-8109-bedcf5911826)

# Simple-Splunk-Setup-Guide
A beginner-friendly guide to setting up Splunk

1. Getting Started
What You'll Need:
Splunk Enterprise installed ( I use the free version for my home lab)

Admin login for Splunk

Your IT system logs (servers, network devices, etc.)


2. Basic Setup Steps
Step 1: Collect Your IT Logs
Go to Settings > Data Inputs

Choose your log type:

For Windows PCs/Servers: Add "Windows Event Logs"

For Network Devices: Add "UDP" (port 514 for syslog)

For Linux: Add monitor to /var/log

Step 2: Create a Ticket Index
Go to Settings > Indexes
Click New Index
Name it it_tickets
Set size limit (e.g., 15GB)

3. Creating Alerts That Make Tickets
Simple Error Alert Example:
  Go to Search & Reporting
  Paste this search: index=your_logs "error" OR "failed" | stats count by host
  Click Save As > Alert

Set:
Alert Name: "Critical Errors"
Trigger When: "Number of results > 5"
Actions: "Send Email" or "Webhook"


4. Connecting to Ticketing Systems
 Email Tickets
 In your alert, choose Send Email
 Enter your help desk email (e.g., helpdesk@darthvader.com)

5 Maintenance Tips

✔ Check daily:

Verify logs are coming in (index=_internal)
Review failed alerts

✔ Clean up:

Archive old tickets monthly
Adjust alert thresholds as needed

Common Issues & Fixes
Problem	                     Solution
No data showing?	    Check firewall rules for log sources
Alerts not working?	  Test webhook/email separately
Splunk running slow?	Reduce log volume or add more RAM



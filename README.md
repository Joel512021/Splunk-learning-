# Spl search query
# Failed logins
index=YOUR_INDEX EventCode=4625 earliest=-24h
| stats count as failed_attempts latest(_time) as last_attempt by host Account_Name Source_Network_Address
| convert ctime(last_attempt)
| sort - failed_attempts


Replace YOUR_INDEX with the index containing your Windows logs. This shows which accounts had the most failures in the past 24 hours, grouped by host and source address. If Account_Name or Source_Network_Address comes back blank, your logs may use different field names; paste one redacted 4625 event and I can adjust the query

(venv) [ec2-user@ip-172-31-24-90 balerica-bank]$ cat /opt/balerica-bank/homework_notes.md
# SEIR Foundations — Lesson 2 Homework
## Seven Alerts, Seven Wins

### Homework 1 — Hello Slack
Successfully sent a personalized alert from my EC2 instance to #balerica-alerts.

### Homework 2 — Severity Tour
INFO, WARNING, ERROR, and CRITICAL alerts were all delivered because the minimum severity was INFO.

### Homework 3 — Server Time
The EC2 server uses UTC, which was six hours ahead of my local Central Standard Time.

### Homework 4 — Disk Watch
Disk usage was 25.4%, resulting in an INFO alert. This is good design because normal conditions should not trigger unnecessary warnings.

### Homework 5 — CPU Load
CPU load was 0.00 / 0.00 / 0.00 on two CPUs. High transaction volume, database queries, or batch processing could increase server load.

### Homework 6 — Incident Drill
Three simulated incidents were delivered:
- DRILL-2941: CRITICAL — Ledger file unreachable.
- DRILL-9231: ERROR — Payment rejection rate above 5%.
- DRILL-6264: WARNING — SWIFT queue reached 42 messages.

The CRITICAL ledger failure deserves an immediate response because it could interrupt essential banking operations. Other incidents should be escalated based on their impact.

### Homework 7 — Morning Report
Successfully delivered a combined monitoring report containing server time, hostname, Python version, disk usage, and CPU load.

### Experiment 1 — Severity Filtering
Prediction: Only CRITICAL alerts would be delivered.
Result: INFO, WARNING, and ERROR were skipped. CRITICAL was delivered.
Conclusion: Severity filtering worked as expected.

### Experiment 2 — Disable Alerts
Changed SLACK_ALERTS_ENABLED to false.
Result: Homework 1 alert was skipped.
Conclusion: The configuration successfully disabled Slack notifications.

### Experiment 3 — Disk Threshold
Changed the WARNING threshold from 75% to 20%.
Result: Disk usage of 25.4% generated a WARNING.
Conclusion: Monitoring thresholds determine alert severity.

### Experiment 4 — Restore Configuration
Restored the disk WARNING threshold to 75%, SLACK_ALERT_SEVERITY to INFO, and SLACK_ALERTS_ENABLED to true.
Result: Disk monitoring returned to INFO and successfully delivered its alert.

### Final Status
All seven homework scripts completed successfully. Slack alerts and monitoring behavior were verified.

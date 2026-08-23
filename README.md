# alex3akeed-uptime

Free uptime monitor for **alex.coralcell.me**, running entirely on GitHub
Actions (public repo → unlimited minutes, no external accounts).

- Every ~10 minutes: `GET /api/health` and `GET /login`, 3 tries each.
- Down → an **[outage] issue** is opened and the run turns red — both email
  the owner. While down, the issue gets a "still down" comment per check.
- Recovered → the issue auto-closes with a timestamp.
- A daily keepalive commit stops GitHub from disabling the schedule after
  60 days of repo inactivity.

Manual check: **Actions → uptime → Run workflow**.

Note: GitHub cron is best-effort — checks can be delayed several minutes.
For tighter detection later, add a free UptimeRobot monitor on the same two
URLs; this repo still covers the alert-by-issue trail.

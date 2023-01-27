# SQL Server Agent
SQL Server Agent is a Microsoft Windows service that executes **scheduled** administrative tasks, which are called *jobs* in SQL Server.

<br>

SQL Server Agent can run a job on a schedule, in response to a specific event, or on demand. For example, if you want to back up all the company servers every weekday after hours, you can automate this task. Schedule the backup to run after 22:00 Monday through Friday. If the backup encounters a problem, SQL Server Agent can record the event and notify you.

## Jobs
A job is a specified series of actions that SQL Server Agent performs. Use jobs to define an administrative task that can be run one or more times and monitored for success or failure. A job can run on one local server or on multiple remote servers.
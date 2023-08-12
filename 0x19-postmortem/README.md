# Postmortem
Learning how to write an Incident Report, also referred to as a Postmortem. This postmortem follows the guidelines used closely by google engineers to file reports. The report is made up of five parts, an issue summary, a timeline, root cause analysis, resolution and recovery, and lastly, corrective and preventative measures. Lets review each of these parts in detail.

## Issue Summary:

Duration: Start Time: May 10, 2023, 14:00 UTC | End Time: May 10, 2023, 17:30 UTC
Impact: Slow Response and Errors on User Dashboard | 35% of Users Affected

## Root Cause: Database Connection Pool Exhaustion

### Timeline:

14:00 UTC: Issue detected as users began reporting slow loading times and errors while accessing the user dashboard.
14:15 UTC: Engineers received monitoring alerts for increased response times and elevated error rates.
14:30 UTC: Initial investigation focused on frontend components and server resources, but no significant anomalies were found.
15:00 UTC: Misleading assumption led to investigating the server logs for unusual spikes, consuming valuable time.
15:45 UTC: Incident escalated to the Database Team to examine database health and performance.
16:15 UTC: Database Team identified database connection pool exhaustion as the root cause.
17:00 UTC: Database Team increased connection pool size and observed gradual improvement in response times.
17:30 UTC: User dashboard performance fully restored, incident resolved.
Root Cause and Resolution:

The root cause of the issue was identified as database connection pool exhaustion. The database server's connection pool size was insufficient to handle the increased number of concurrent user requests during peak hours. As a result, users experienced slow loading times and errors while accessing their dashboards.

To resolve the issue, the Database Team increased the connection pool size and optimized the connection reuse process. This change allowed the database server to handle the higher demand for connections during peak times without causing exhaustion. Once the pool size was adjusted, the user dashboard's response times gradually improved, and users reported a better experience.

## Corrective and Preventative Measures:

Increase Connection Pool Size: Permanently adjust the connection pool size to accommodate peak user traffic and prevent future connection exhaustion.
Implement Dynamic Scaling: Explore implementing auto-scaling mechanisms for both frontend and backend components to handle varying levels of user traffic automatically.
Enhance Monitoring: Implement advanced monitoring and alerting systems that can proactively detect and notify teams about resource exhaustion and performance anomalies.
Database Optimization: Continuously monitor database performance and optimize query execution plans to ensure efficient use of resources.
Regular Load Testing: Conduct regular load testing to identify potential bottlenecks and capacity limits before they impact user experience.
Incident Response Training: Conduct training sessions to improve incident detection, escalation, and resolution processes across teams.

In conclusion, the user dashboard slowdown was caused by a database connection pool exhaustion due to inadequate sizing for peak user demand. The incident highlighted the importance of efficient resource management, proactive monitoring, and collaboration among teams. By implementing corrective and preventative measures, we aim to ensure a seamless user experience during peak usage periods and maintain the reliability of our services.

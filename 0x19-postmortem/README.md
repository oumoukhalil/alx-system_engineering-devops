
WordPress website - Apache2 Web Service Incident report
Adam Sanusi Babatunde
Adam Sanusi Babatunde
Tutor | Software Engineering Student | Back-End Developer
4 articles 
Suivre
20 janvier 2024

Ouvrir le lecteur immersif

Introduction:
In the world of DevOps and SysAdmin, even the most seasoned professionals encounter unforeseen challenges. In this incident report, we unravel a real-time scenario where a WordPress website, fueled by a LAMP stack, grappled with 22-minute period of 500 internal error messages. Join us on a journey through the timeline, root cause analysis, and the valiant efforts to resurrect the website.
Issue Summary 
From 10:28 AM to 10:50 AM, Users using my WordPress site had 500 internal error messages. So I made a maintenance check on the Apache server and it was returning a 500 error whenever I ran it on a local host (curl -sI 127.0.0.1).
The root cause of this issue was an invalid configuration change due to a typo error in the /var/www/html/wp-settings.php configuration.

Timeline:
10:25 AM: Unassuming Configuration Push Begins
10:28 AM: Outage Unleashed
10:30 AM: The Race to Resolve Kicks Off
10:35 AM: Tracing the Apache2 Process
10:42 AM: Failed Attempts and Frustration
10:47 AM: Spotting the Culprit
10:50 AM: Victory Achieved, Apache2 Runs with a Proud Status 200
Root Cause and Resolution:
At the core of this incident was a configuration change gone awry. Without a safety net of a thorough testing phase, a change was unleashed into the production environment at 10:25 AM. This change, specifying a file access error in the WordPress configuration settings, left the server unable to read from the unknown file. A simple typo error on a line further complicated matters, causing a cascade effect that led to a failed fix attempt.
As the 500 errors surfaced at 10:28 AM, our protagonist (the site administrator) swiftly initiated a maintenance check. With no rollback configuration available, a manual inspection of the configuration ensued. The Apache2 process was inspected, leading to a brief moment of hope at 10:42 AM, where an assumption about missing files was made and quickly dispelled.
It wasn't until 10:47 AM that the needle in the haystack was found – a typo error in the /var/www/html/wp-settings.php file. 

The server, desperately trying to find a misspelled file, was throwing a tantrum. A swift fix, executed at 10:50 AM, restored the correct web pages and brought the server back to life, now responding with the coveted status 200.

Corrective and Preventive Measures:
After the fix, the following are actions I was taken to address the issue and help prevent recurrence:
1. Rollback Protocols: Instituted a robust rollback process to swiftly undo changes causing disruptions.
2. Monitoring Services: Implemented a proactive monitoring service for read-and-write operations, ensuring prompt detection of anomalies.
Conclusion:
Challenges are inevitable, but how we navigate them defines our expertise. This incident report serves not only as a post-mortem analysis of a WordPress website's hiccup but also as a beacon of learning for developers and administrators alike. Remember, even in the face of a 500 internal error, with a vigilant eye and strategic measures, victory can be snatched from the jaws of defeat. Happy coding!

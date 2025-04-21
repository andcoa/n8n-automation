# n8n automation

## Objective

To build automated security workflows integrated with the NixGuard API to streamline detection, alerting, and response actions in a SOC environment. The goal was to reduce manual analyst workload by automating repetitive security operations such as log ingestion, threat identification, and incident notification.

## Skills Learned

- Workflow Design: Created multi-step, event-driven workflows to automate the collection, analysis, and response to security events using visual flow logic.
- API Integration: Connected n8n to the NixGuard API using HTTP Request nodes, passing dynamic parameters and handling authentication securely.
- Threat Intelligence Automation: Automated threat lookups, IP analysis, and alerting processes for real-time security monitoring and response.
- Automated Notifications: Integrated conditional logic and trigger nodes to send alerts (e.g., via email or webhook) when specific threats or anomalies were detected.
- Testing & Debugging: Tested and optimized each step of the workflow to ensure data integrity, correct parsing of API responses, and efficient error handling.

## Tools Used
- n8n – Low-code workflow automation platform used to build and orchestrate automated threat response workflows.

## Steps

Built the following workflow to automate log analysis and fine tune alerts based on the findings.

![image](https://github.com/user-attachments/assets/8f61ff30-f43c-4b61-924a-1db6400be648)

Breakdown of the workflow:
-	Interval Trigger: Every minute the automation would be triggered to get data from NixGuard.
-	HTTP Request: GET Request to get new Nix alerts.
-	Function Block: Convert Nix data into proper format to be submitted into Virus Total or any repository.
-	Virus Total: Submit the transformed data to Virus Total for analysis.
-	Switch Block: Route Virus Total data based on parameters.
-	Send Email: If Virus Total returns a positive value, the workflow would send an email to the analyst.
-	HTTP Post: POST Request to send new details about the alert back into the SIEM.

The workflow can be configured according to the type of alerts pulled from NixGuard and send emails to the analyst or update the SIEM based on the Network Analysis and Threat Detection parameters provided. For the Incident Response automation, two new blocks would be added:

-	OpenAI Message Model: Write an Incident Response Plan based on Virus Total data.
-	Edit Field Block: Summarize the Incident Response Plan and email it to the analyst.

![image](https://github.com/user-attachments/assets/90ca2736-f877-439b-a64d-4c88c7e4f27e)

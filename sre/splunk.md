



The New Kubernetes Monitoring Experience in Splunk Observability Cloud      
https://www.youtube.com/watch?v=QgRKBB9hW5Q  


Naresh i Technologies    
Mastering Splunk A Hands On Real Time Monitoring and Analytics   
https://youtu.be/Quc24xptj-4?si=egro6J4FBAYxMqzZ    

Observability in Action | Session 2 | Veerababu   
https://www.youtube.com/watch?v=ZwkqgvftazA    

Simplify AIOps with Universal Alerting   
https://www.youtube.com/watch?v=xZlEamyzKDc&t=452s     

**Splunk Observability Cloud Free Edition**    
https://www.splunk.com/en_us/download/o11y-cloud-free-trial.html     
Suggest beginner-friendly projects to build in your splunk free account     

splunk search processing language   
splunk take log from server eg /var/logs and forward to splunk    
splunk forwarder     

▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄    
══+════════════════════════════════════════    
When Would Someone Mix Splunk, 
Prometheus, and Grafana?While Splunk doesn't need Prometheus to talk to Grafana, you might occasionally see all three tools mentioned in the same engineering architecture. This happens for two specific reasons:    
1. Splunk and Prometheus are handling different data types
   - Prometheus handles real-time metrics (numbers, CPU stats, GPU temps) because it is incredibly fast and cheap to store.
   - Splunk handles logs and security events (text data, application stack traces, access logs) because it excels at searching text.
   - Grafana sits on top of both of them, acting as a single pane of glass showing metrics from Prometheus and logs from Splunk side-by-side on the same screen.

2.  Splunk can acting as the long-term storage for Prometheus := Some organizations use Prometheus to scrape raw metrics locally, but then use Prometheus's Remote Write feature to automatically send those metrics into Splunk (using Splunk's Metrics Index). In this case, Grafana would pull the historical metrics directly out of Splunk.
3.  
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
- In Splunk, the tool that collects server metrics (like CPU and memory) is the **Splunk Universal Forwarder or the Splunk Distribution of OpenTelemetry**      Collector.
- Splunk Observability Cloud collects server metrics primarily using the Splunk Distribution of the OpenTelemetry Collector. Deployed on each host as a lightweight agent, it scrapes system resources like CPU, memory, disk I/O, network traffic, and process counts. The Collector then processes and securely pushes this data to the platform.
- - Collection: It uses built-in features called scrapers (or plug-ins) to pull data directly from the host's operating system.
  - Publishing: The collector actively pushes (streams) this metric data in real-time directly to the Splunk Observability Cloud.   

-  How the **Universal Forwarder Works (Classic Splunk Enterprise)**
- - Collection: It uses local system commands to monitor performance. On Linux, it runs scripts or uses the Splunk Add-on for Unix.
  - Publishing: The forwarder constantly pushes the data over TCP (usually port 9997) to your central Splunk Indexer, where it is written to the database.








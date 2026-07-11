



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

2.  Splunk can acting as the long-term storage for Prometheus
    Some organizations use Prometheus to scrape raw metrics locally, but then use Prometheus's Remote Write feature to automatically send those metrics into Splunk (using Splunk's Metrics Index). In this case, Grafana would pull the historical metrics directly out of Splunk.
3.  

▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     








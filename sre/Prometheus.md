
**Node Exporter**    
- Node Exporter is an official project maintained by the Prometheus team. It is an agent that runs on your servers and translates system-level hardware metrics (CPU, memory, disk, network) into a format that Prometheus can read and collect.Node Exporter (The Collector): Acts as your server's "sensors." It reads current machine metrics and exposes them on a local web page (usually port 9100). It does not store or analyze this data itself.
   

**Prometheus (The Collector & Database):**    
- Acts as the central "brain." It goes out to your servers at regular intervals, pulls (scrapes) the data from Node Exporter, stores it historically as a time-series database, and allows you to query it for alerts and dashboards.     

Node Exporter:-    
- Primary Role:= Collect hardware and OS metrics (CPU, RAM, disk).   
- Execution := Runs as a lightweight agent on the target machine.
- Storage := Stateless; only displays current metrics in real-time.
- Data Flow := Exposes an HTTP /metrics endpoint for Prometheus to pull.

Prometheus :-
- Primary Role:= Scrape, store, query, and alert on metrics.         
- Execution := Runs centrally as a server or cluster application.     
- Storage := Stateful; stores data over time using a time-series database.     
- Data Flow := Initiates the scrape and saves the data.     
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     
══+════════════════════════════════════════       
Prometheus, Node Exporter & Grafana Setup on Linux | Complete Monitoring Stack with systemd    
https://www.youtube.com/watch?v=sGMXsUTEVr0     




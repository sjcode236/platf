
**- To visualize your Prometheus and Node Exporter metrics, Grafana sits on top of Prometheus as the user interface**  
- Think of Grafana as the dashboard/display screen of your car, while Prometheus remains the computer storing the data. Grafana does not talk to Node Exporter directly; it asks Prometheus for the data and turns it into graphs     
══+════════════════════════════════════════    
Step 1: Connect Grafana to Prometheus (Add Data Source)     
- Before making dashboards, you must tell Grafana where your Prometheus server is living.    
- 1. Open your Grafana web interface (usually http://localhost:3000).    
  2. click the Burger Menu (☰) in the top-left corner and go to Connections > Data sources.
  3. Click Add data source.
  4. Select Prometheus from the list.
  5. In the Connection section, enter your Prometheus URL (e.g., http://localhost:9090 or http://<your-prometheus-ip>:9090).
  6. Scroll to the bottom and click Save & test. You should see a green checkmark saying "Data source is working".   

Step 2: Use a Pre-built Node Exporter Dashboard (Recommended)    
=You don't need to build charts for CPU, RAM, and Disk from scratch. The community has already built highly detailed, production-ready dashboards for Node Exporter. 
1. Go to the official Grafana Dashboard Library
2. Search for "Node Exporter Full" (Dashboard ID 1860 is the most popular and comprehensive choice).
3. Copy the Dashboard ID (1860).
4. Go back to your Grafana interface.
5. Click the Plus (+) icon or Dashboards in the sidebar, and select Import.
6. Paste the ID 1860 into the "Import via grafana.com" field and click Load.
7. On the next screen, select your Prometheus data source from the dropdown menu at the bottom.
8. Click Import.
Your dashboard will instantly populate with live graphs showing your server's CPU usage, memory, disk I/O, and network traffic.
 
Step 3: How Grafana Asks Prometheus for Data (The Logic)    
If you ever want to create your own custom graph panel, Grafana uses PromQL (Prometheus Query Language) to pull the data.    
When you click "Add Visualization" inside a dashboard, Grafana will open a query builder. You type a PromQL metric name into the query box, and Prometheus sends back the numbers.    
Common Node Exporter PromQL Examples:    
=Total RAM Used %: (node_memory_MemTotal_bytes - node_memory_MemAvailable_bytes) / node_memory_MemTotal_bytes * 100   
=CPU Idle %: sum by (instance) (rate(node_cpu_seconds_total{mode="idle"}[5m]))    
=Disk Space Usage %: 100 - ((node_filesystem_avail_bytes{mountpoint="/"} * 100) / node_filesystem_size_bytes{mountpoint="/"})    











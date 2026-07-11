
**- To visualize your Prometheus and Node Exporter metrics, Grafana sits on top of Prometheus as the user interface**  
- Think of Grafana as the dashboard/display screen of your car, while Prometheus remains the computer storing the data. Grafana does not talk to Node Exporter directly; it asks Prometheus for the data and turns it into graphs

Step 1: Connect Grafana to Prometheus (Add Data Source)     
- Before making dashboards, you must tell Grafana where your Prometheus server is living.    
- 1. Open your Grafana web interface (usually http://localhost:3000).    
  2. click the Burger Menu (☰) in the top-left corner and go to Connections > Data sources.
  3. Click Add data source.
  4. Select Prometheus from the list.
  5. In the Connection section, enter your Prometheus URL (e.g., http://localhost:9090 or http://<your-prometheus-ip>:9090).
  6. Scroll to the bottom and click Save & test. You should see a green checkmark saying "Data source is working".   
Step 2: Use a Pre-built Node Exporter Dashboard (Recommended)
- 





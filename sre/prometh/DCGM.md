
**-  DCGM = Data Center GPU Manager   -**    
Pulling NVIDIA GPU telemetry from DCGM Exporter into Prometheus and visualizing it in Grafana follows the exact same architectural logic as Node Exporter, but operates on Port 9400.

Step 1: Verify DCGM Exporter is Running     
Before configuring Prometheus, ensure your NVIDIA DCGM Exporter is running and exposing metrics on your GPU server.    
Run this command on your GPU machine to verify:     
- curl http://localhost:9400/metrics
- Expected Result: You should see text output filling your terminal screen with lines like DCGM_FI_DEV_GPU_UTIL and DCGM_FI_DEV_MEM_COPY_UTIL.    

Step 2: Configure Prometheus to Scrape DCGM Exporter     
You need to tell Prometheus to target port 9400 on your GPU server.    
1. Open your prometheus.yml configuration file on your Prometheus server.
2. Under the scrape_configs: section, add a new job block:
```
yaml
scrape_configs:
  - job_name: 'dcgm-exporter'
    scrape_interval: 15s
    static_configs:
      - targets: ['<YOUR-GPU-SERVER-IP>:9400']
```
3. Restart your Prometheus service to apply the changes:
    sudo systemctl restart prometheus
4. Verify the connection: Open your Prometheus Web UI (http://<prometheus-ip>:9090), navigate to Status > Targets, and ensure dcgm-exporter is listed as UP.

Step 3: Import the Official NVIDIA Dashboard in Grafana   
=NVIDIA provides a pre-built, production-grade Grafana dashboard designed specifically for DCGM Exporter.   


  

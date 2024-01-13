# 11_setup_grafana02
Let's continue setting up Grafana for the ELK Stack, which can capture logs from your application and convert them into dashboards for monitoring purposes.
![Slide11](https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/645add32-b6c3-48e6-99cc-44a42eed74a9)

## Objectives
- Set up Grafana Datasource: Elasticsearch - to monitor the logging of your application and create new dashboards from them.
- Learn how to use Grafana to set up a monitoring solution for your system.

## Expected Outcome
- Grafana is ready to use.

## Prerequisites
- Must finish task: 
    - 08_setup_kibana-elk
    - 09_setup_filebeat

## Step-by-Step: How to setup datasource Elasticsearch on Grafana
> [!NOTE]
> The following instruction for the [Grafana] only.
### Access Grafana URL
```sh
http://<public-ip-address>:3000/grafana
```

### Setup Elasticsearch datasource on Grafana
<img width="869" alt="grafana-elk01" src="https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/54c2689f-1579-48c2-a59c-0bf3ede50902">

1. Access the Data Sources Section:In Grafana, click on the gear icon (⚙️) in the left sidebar to open the main menu.  Select "Data Sources" under the "Configuration" section. 
2. In the "Choose a data source" section, search for "Elasticsearch" or scroll down to find it.Click on the Elasticsearch option. 
3. In the "HTTP" section, provide the URL of your Elasticsearch cluster. It should look like https://13.214.58.236:9200 
4. If you are using HTTPS, check the "Enable TLS" box and provide the necessary information. 
5. Scroll down to the "Auth" section if you have authentication enabled on your Elasticsearch cluster. Provide the username and password. 
6. Elasticsearch details
    - Index name 
    - Time field name    
   <img width="428" alt="grafana-elk02" src="https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/dc39aeae-62ac-41c2-8eb1-60f3d7061670">
8. Click on "Save & Test" to verify the connection. If everything is set up correctly.

## Step-by-Step: How to Create Visualizations on Grafana Dashboard Using Elasticsearch Datasource


1. In Grafana, navigate to the "New" icon on the left sidebar and click on "Dashboard" to create a new dashboard. 
2. Click on "Add visulization." 
3. In the panel settings, you need to select the Elasticsearch data source you added earlier. 
4. Choose the appropriate index pattern and configure the query to retrieve the data you want to visualize. 
5. Choose the visualization type that suits your data. Grafana supports various visualization types such as Graph, Singlestat, Table, etc. 
6. Configure the axes, legend, and other visualization options based on your requirements.

# 📌 Must Have !! 
- [ ] 1.Create a requirement visualization to display the "HTTP response code" of WordPress as shown below:

![grafana elk03](https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/ac4ae92f-6e1c-4805-b005-12c14557ed83)

- [ ] 2.Create a requirement visualization to display the "HTTP Responsetime by service" of WordPress as shown below:
<img width="703" alt="elastic-query" src="https://github.com/chayapon-s/kbtg-infra-kampus-bootcamp2024/assets/49383429/786d7ad7-6df3-454b-a956-ebfacb0e89fe">



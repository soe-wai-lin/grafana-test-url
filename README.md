 ## To test this project,need preinstall docker and docker-compose in your environment ##

 systemctl status docker  { docker service should up and running }

 docker compser version   { Check "docker compose" }

 ## make sure to open firewall port 9090 for prometheus, 3000 for grafana and 9115 for blackbox. ##

 firewall-cmd --add-port=9090/tcp --add-port=3000/tcp --add-port=9115/tcp --permanent

 firewall-cmd --reload

 firewall-cmd --list-port       {check the port that you opened}

 ## Go to directory that exist docker-compose.yaml ##
 
 docker compose up -d           { if "docker compose" command does not work, try "docker-compose up -d" }

 docker compose ps              { must be running Three containers and "Network grafana-test-url_monitoring" }

 ## Recheck requirement ports ##

 ss -tunlp | grep 9090

 ss -tunlp | grep 9115

 ss -tunlp | grep 3000

 ## Open grafana, prometheus and blackbox in browser ##

 If you test it on server, for prometheus "http://server-ip:9090" , for grafana "http://server-ip:3000"

 If you test it on laptop, for prometheus "http://localhost:9090", for grafana "http://localhost:3000"

 ## Set up Grafana with prometheus ##

 browse grafana URL , for example "http://server-ip:3000"

 "username: admin"
 
 "password: grafana"

 Click on : Data Sources >>  Add data soruce >> Prometheus >> Prometheus Server URL under Connection: "ADD YOUR Prometheus Server IP" >> Save and Test

 Click on : Dashboards >> Create Dashboard >> Import Dashboard >> paste "7587" >> load >> choose "Prometheus" in Select prometheus data source" >> import

 ## NOTE ##

 When you import dashboard with ID "7587" that show above, you can choose yourself as you like Dashboard , please check "https://grafana.com/grafana/dashboards/?search=blackbox"

 If you want add more URL, you can add into "prometheus.yml" and restart prometheus service.

 docker composer restart prometheus

 

 

 
 


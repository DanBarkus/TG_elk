# TigerGraph Logs with Kibana
- Used for bare metal installations of TigerGraph
- Can be used with any 3.x version of TigerGraph
- Code for selecting which logs are read can be found in `filebeat/config/filebeat.yml`
- Code for filtering logs can be found in `logstash/pipeline/logstash.conf`

***
## Requirements
This app requires:
 - Bare metal install of TigerGraph
 - TigerGraph to be a 3.x version
 - Docker to be installed on the server
***
## Commands for running ELK with TigerGraph
Start docker daemon:
```console
$ sudo systemctl start docker
```

Start Docker containers:
```console
$ sudo docker-compose up -d
```

Stop Docker containers:
```console
$ sudo docker-compose down -v
```

Reset Kibana password:
```console
$ sudo docker-compose exec elasticsearch bin/elasticsearch-reset-password --batch --user elastic
```

***
## Kibana Dashboard Creation
Once the app is up and running, a sample dashboard can be used for viewing the logs. To Install the sample dashboard:
- Open Kibana at https://localhost:5601
- Log in with credentials:
    - username: elastic
    - password: (password generated from command in previous section)
- Go to "Saved Objects" page
- Click "Import" and choose the file found in `kibanaDashboardSample` folder
- Navigate to "Dashboard" page
- Select"MyExampleDashboard" from list of options

Once on dashboard page, time filter may need to be updated to show a larger time window for logs to appear

***
## TigerGraph Log Sources
This is where you can find the log files within your TigerGraph install associated with the queries in case you wish to read the logs themselves
- API endpoint logs: `log/restpp/RESTPP#1.INFO`
- Graph Studio logs: `log/gui/GUI#1.out`

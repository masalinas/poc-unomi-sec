# Description
PoC Apache Unomi Securized

# Start Apache Unomi
Execute this command:

```
docker compose up -d
```

### Check cluster and send some requests
To access to any Unomi resource we will use the default credentials as basic authentication:
- **Username**: karaf
- **Password**: karaf

Check cluster status from browser:
```
https://localhost:9444/cxs/cluster
```

Access to Unomi swagger API:
```
https://localhost:9444/cxs/api-docs
```

Using curl list cluster info or postman we must use the default credentials:
```
curl -X GET --insecure -u karaf:karaf -H "Accept: application/json" https://localhost:9444/cxs/cluster
```

# Start WSO2 API Manager Server (wso2-am) (AM)
We start WSO2 in a the port 9446 from the default 9443. We will use the 9446 configuring the **deployment.tom** file adding offset attribute like this:

```
[server]
hostname = "localhost"
offset=3
base_path = "${carbon.protocol}://${carbon.host}:${carbon.management.port}"
#discard_empty_caches = false
server_role = "default"
```

```
docker run -it --name poc-wso2-am -d -p 8280:8280 -p 8243:8243 -p 9446:9446 --volume $PWD/deployment-am.toml:/home/wso2carbon/wso2am-4.0.0/repository/conf/deployment.toml wso2/wso2am:4.0.0
```
To access to Management Console UI: https://localhost:9444/carbon
To access the API Manager Publisher: https://localhost:9444/publisher
To access the API Manager Developer Portal: https://localhost:9444/devportal
- **Username**: admin
- **Password**: admin

# Start WSO2 Indentity Server (wso2-is) (IAM)
We start WSO2 in a the port 9445 from the default 9443. We will use the 9445 configuring the **deployment.tom** file adding offset attribute like this:

```
[server]
hostname = "localhost"
node_ip = "127.0.0.1"
base_path = "https://$ref{server.hostname}:${carbon.management.port}"
offset = 2
```

```
docker run -it --name poc-wso2-is -d -p 9445:9445 --volume $PWD/deployment-is.toml:/home/wso2carbon/wso2is-7.0.0/repository/conf/deployment.toml wso2/wso2is:7.0.0
```

Access to Management Console UI: https://localhost:9445/carbon

In this version exist a new Management Console UI located under /console path: https://localhost:9445/console

The default credentials to access is:
- **Username**: admin
- **Password**: admin

# Start HAProxy

# Links

Some links:

- [WSO2 Documentation](https://is.docs.wso2.com/en/latest/)
- [WSO2 Docker](https://hub.docker.com/r/wso2/wso2is)
- [HAProxy Docker](https://hub.docker.com/_/haproxy)

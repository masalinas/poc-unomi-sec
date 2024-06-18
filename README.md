# Description
PoC Apache Unomi Securized

# Start Apache Unomi service
Execute this command:

```
docker compose up -d
```

# Check cluster and send some requests
To access to any Unomi resource we will use the default credentials as basic authentication:
**Username**: karaf
**Password**: karaf

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

# Start WSO2 IAM Indentity Server Manager (IAM)
We start WSO2 in a different port tham 9443. Ww will use the 9445 configuring the **deployment.tom** file adding offset attribute like this:

```
[server]
hostname = "localhost"
node_ip = "127.0.0.1"
base_path = "https://$ref{server.hostname}:${carbon.management.port}"
offset = 2
```

```
docker run -it --name consum-wso2 -d -p 9445:9445 --volume /mnt/c/git/poc-unomi-sec/deployment.toml:/home/wso2carbon/wso2is-7.0.0/repository/conf/deployment.toml wso2/wso2is:7.0.0
```

Access to Management Console UI. In this version exist a new one:
[Old WSO2 Management Console UI](https://localhost:9445/carbon)
[New WSO2 Management Console UI](https://localhost:9445/console)

**Username**: admin
**Password**: admin

# Start HAProxy

# Links

Some links:

- [WSO2 Documentation](https://is.docs.wso2.com/en/latest/)
- [WSO2 Docker](https://hub.docker.com/r/wso2/wso2is)
- [HAProxy Docker](https://hub.docker.com/_/haproxy)

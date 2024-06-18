# Description
PoC Apache Unomi Securized

# Start Apache Unomi service
Execute this command:

```
docker compose up -d
```

# start WSO2 IAM Indentity Server Manager (IAM)
```
docker run -it --name consum-wso2 -d -p 9445:9443 wso2/wso2is:7.0.0
```

Access to Management Console (Carbon)
[WSO2 Management Console](https://localhost:9445/carbon/admin/login.jsp)

**Username**: admin
**Password**: admin

# Links

Some links:

- [WSO2 Docker](https://hub.docker.com/r/wso2/wso2is)

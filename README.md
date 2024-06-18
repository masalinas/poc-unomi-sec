# Description
PoC Apache Unomi Securized

# Start Apache Unomi service
Execute this command:

```
docker compose up -d
```

# Start WSO2 IAM Indentity Server Manager (IAM)
```
docker run -it --name consum-wso2 -d -p 9445:9445 --volume /mnt/c/git/poc-unomi-sec/carbon.xml:/home/wso2carbon/wso2is-7.0.0/repository/conf/carbon.xml wso2/wso2is:7.0.0
```

Access to Management Console (Carbon)
[WSO2 Management Console](https://localhost:9445/carbon/admin/login.jsp)

**Username**: admin
**Password**: admin

# Start HAProxy

# Links

Some links:

- [WSO2 Documentation](https://is.docs.wso2.com/en/latest/)
- [WSO2 Docker](https://hub.docker.com/r/wso2/wso2is)
- [HAProxy Docker](https://hub.docker.com/_/haproxy)

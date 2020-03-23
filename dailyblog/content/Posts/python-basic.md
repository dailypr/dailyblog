---
title: "Python Basic"
date: 2020-03-23
tags: [python]
---

# How to handle json file

- If you want to get `PublicIp` from the json file below ...

```
$ test.json 
{
    "NatGateways": [
        {
            "NatGatewayAddresses": [
                {
                    "PublicIp": "", 
                    "NetworkInterfaceId": "", 
                    "AllocationId": "", 
                    "PrivateIp": "
                }
            ], 
            "VpcId": ", 
            "Tags": [], 
            "State": "", 
            "NatGatewayId": "", 
            "SubnetId": "", 
            "CreateTime": "2"
        }, 
        {
            "NatGatewayAddresses": [
                {
                    "PublicIp": "", 
                    "NetworkInterfaceId": "", 
                    "AllocationId": “”, 
                    "PrivateIp": ""
                }
            ], 
            "VpcId": "", 
            "Tags": [], 
            "State": "", 
            "NatGatewayId": "", 
            "SubnetId": "", 
            "CreateTime": ""
        }
    ]
}
```

```
import json

with open('iot-releng-seoul.json') as json_file:
    json_data = json.load(json_file)
    for nat in json_data['NatGateways']:
        print( nat['VpcId'] ,nat['NatGatewayAddresses'][0]['PublicIp'] )
```
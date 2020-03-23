---
title: "Helm - Remember me"
date: 2020-03-22
tags: [helm,cmd]
---

# Common

helm ls  
helm ls  --all

helm get datadog-eks14  

helm delete [HELM RELEASE NAME] 
helm del --purge xxxxx    

helm install ./test-chart --name test-chart-release   
helm install -f ./xxxxxx/values.yaml --name xxxxxxx ./xxxxxx  

helm uninstall 
---
title: "k8s - Managing Multi Clusters"
date: 2020-03-22
tags: [k8s]
---

# Basic Way
---

1. Create config files in `~/.kube` folder.  
```
~/.kube  
$ ll
eu02d_config
na03d_config
na03s_config
relengd_config
```

2. Add below code to `~/.zshrc`.   
```
##-------- k8s config
export KUBECONFIG=~/.kube/config:~/.kube/na03s_config:~/.kube/relengd_config:~/.kube/eu02d_config:~/.kube/na03d_config:
```

3. `source ~/.zshrc`  

4. Verify all the contexts using the command below.   
```
$ kubectl config get-contexts
CURRENT   NAME                         CLUSTER                      AUTHINFO                     NAMESPACE
          eks14-eu02d_euwest1          eks14-eu02d_euwest1          eks14-eu02d_euwest1          
          eks14-na03d_useast2          eks14-na03d_useast2          eks14-na03d_useast2          
          eks14-na03s_useast2          eks14-na03s_useast2          eks14-na03s_useast2          
*         eks14-relengd_apnortheast2   eks14-relengd_apnortheast2   eks14-relengd_apnortheast2

```

5. Change the context using the command below and verify current context.    
```
$ kubectl config use-context eks14-na03s_useast2
Switched to context "eks14-na03s_useast2".

$ kubectl config current-context
eks14-na03s_useast2
```


# Tool - kubectx
---

1. Install kubectx.  
- https://github.com/ahmetb/kubectx  

2. Change context using `kubectx` command.  
```
$ ~/kubectx
eks14-eu02d_euwest1
eks14-na03d_useast2
eks14-na03s_useast2
eks14-relengd_apnortheast2
 
$ ~/kubectx eks14-na03s_useast2
Switched to context "eks14-na03s_useast2".

```
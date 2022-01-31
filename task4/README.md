# Homework
## deploy_view and deploy_edit
```fish
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[16:51:25]─[G:master=]
╰─>$ kubectl config use-context deploy_view
Switched to context "deploy_view".
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[16:51:57]─[G:master=]
╰─>$ kubectl get deployment
NAME           READY   UP-TO-DATE   AVAILABLE   AGE
minio          1/1     1            1           44h
web            3/3     3            3           25h
web-emptydir   2/2     2            2           24h
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[16:52:00]─[G:master=]
╰─>$ kubectl get pod
NAME                            READY   STATUS    RESTARTS      AGE
dnsutils                        1/1     Running   2 (44h ago)   2d23h
minio-575d987896-9tt7r          1/1     Running   1 (44h ago)   44h
nginx                           1/1     Running   2 (44h ago)   3d2h
web-5584c6c5c6-7vwvs            1/1     Running   0             25h
web-5584c6c5c6-9bsnm            1/1     Running   0             25h
web-5584c6c5c6-p4sfb            1/1     Running   0             25h
web-emptydir-6f875dfdf6-4cfct   1/1     Running   0             24h
web-emptydir-6f875dfdf6-bh698   1/1     Running   0             24h
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[16:52:07]─[G:master=]
╰─>$ kubectl get svc
Error from server (Forbidden): services is forbidden: User "deploy_view" cannot list resource "services" in API group "" in the namespace "default"
```

```fish
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[16:56:55]─[G:master=]
╰─>$ kubectl config use-context deploy_edit
Switched to context "deploy_edit".
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[16:57:20]─[G:master=]
╰─>$ kubectl auth can-i "*" deployment
yes
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[16:57:35]─[G:master=]
╰─>$ kubectl auth can-i "*" pods
yes
```
## prod_admin and prod_view
```fish
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[20:23:35]─[G:master=]
╰─>$ kubectl config use-context prod_admin
Switched to context "prod_admin".
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[20:23:47]─[G:master=]
╰─>$ kubectl auth can-i "*" "*" --namespace prod
yes
```

```fish
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[20:23:50]─[G:master=]
╰─>$ kubectl config use-context prod_view
Switched to context "prod_view".
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[20:25:24]─[G:master=]
╰─>$ kubectl auth can-i "*" "*" --namespace prod
no
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[20:25:27]─[G:master=]
╰─>$ kubectl auth can-i "get" "*" --namespace prod
yes
┬─[unforgiven@mint-pc:~/M/e/k/h/task4]─[20:25:32]─[G:master=]
╰─>$ kubectl auth can-i "list" "*" --namespace prod
yes
```
## Service account
```fish
┬─[unforgiven@mint-pc:~/M/e/k8s]─[12:48:55]
╰─>$ kubectl config use-context sa-namespace-admin
Switched to context "sa-namespace-admin".
┬─[unforgiven@mint-pc:~/M/e/k8s]─[12:49:02]
╰─>$ kubectl auth can-i "*" "*"
yes
```
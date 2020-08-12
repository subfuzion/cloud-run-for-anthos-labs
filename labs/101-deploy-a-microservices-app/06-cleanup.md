# Clean up

1\. If you made any DNS changes to a domain under your control when you
 published the app, you should remove those records now.

2\. If you just want to delete the app but leave the cluster running, just run
 the following commands:
 
```
kubectl delete -f knative/v2/
kubectl delete -f kubernetes/
```

3\. If you want to delete the entire cluster:

```
gcloud container clusters delete cluster-1
```


---
[[toc]](README.md) [[back]](05-autoscaling.md)


## Hello Minikube Reflections

1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app? 

* Before:
![before](assets/1-logs-before.png)
* After:
![after](assets/1-logs-after.png)

Each time the application is accessed, it generates a log entry `GET /` for the incoming request, which is captured in the logs of the corresponding Pod.

2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created? 

The `-n` or `--namespace` option in kubectl is used to specify the Kubernetes namespace in which to perform operations. When not specifying a namespace, kubectl defaults to the default namespace. Running `kubectl get -n kube-system` lists resources in the kube-system namespace, which contains system components rather than user-created resources.
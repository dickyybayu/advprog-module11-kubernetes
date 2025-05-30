# Reflection: Hello Minikube - Advanced Programming Module 11

## 1. Compare the application logs before and after exposing it as a Service

Before exposing the application as a Service, the logs only showed startup messages such as:

![kubebefore](images/kubectlbeforeexposed.png)

After exposing the app using `kubectl expose` and running `minikube service hello-node`, I accessed the app through the browser multiple times. The logs increased with entries like:

![kubeafter](images/kubectlafterexposed.png)

This shows that every time the app was opened in the browser, a new log entry appeared. This means the Service successfully exposed the Pod to external traffic, and each incoming request was logged by the container.


## 2. What is the purpose of the `-n` option in `kubectl get`?

Using `kubectl get` without the `-n` flag shows resources from the **default namespace**, which is where my `hello-node` deployment and service were created by default.

![kubedefaultnamespace](images/kubegetdefaultnamespace.png)

When I used:
kubectl get pods,services -n kube-system

![kubedefaultnamespace](images/kubegetwithnamespace.png)

it only showed system-managed components like metrics-server, kube-dns, etcd, and kube-apiserver.

That's because those resources belong to the kube-system namespace, not the default one.

In short, the -n flag lets me choose which namespace I want to look at, and that’s why I didn’t see my app when querying the kube-system namespace.



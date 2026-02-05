# Diagnosing CrashloopBackoffs and ImagePullBackoffs 🚨

When working with Kubernetes, encountering pod issues like CrashLoopBackOff and ImagePullBackOff is common. Here's how to diagnose and resolve these issues effectively. The most important priority is containing the blast radius and making sure other workloads within your namespace are not effected. Next the deployment needs to be rolled back to minimize downtime so user experiences isn't effected. 

# CrashLoopBackOff ⚠️

A CrashLoopBackoff happens when the container image is pulled successfully by the kubelet but immediately exit repeatedly 

Causes ✅
 
 - Application panics and throws a fatal error 

- Port is not available 

- Invalid args or sh commands in your pod

- ConfigMap or PVC mounted on wrong mouth path. 

# ImagePullBackoff ⚠️

An ImagePullBackoff happens when kubelet is not able to the container image from the registry

Causes ✅

- Incorrect name/tag

- Image does not exist

- node unable to reach registry DNS, Proxy or Ingress

# Diagnosis and Logs 🛠️

```bash 
kubectl logs -f <pod> -n <namespace>
kubectl describe pod <pod> -n <namespace>
kubectl logs deploy/<deployment> 
kubectl get pods -A -o wide
```

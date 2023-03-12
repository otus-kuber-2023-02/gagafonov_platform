# gagafonov_platform
gagafonov Platform repository

## kubernetes-intro

list of pods in ns kube-system

- **coredns-787d4945fb-8rmn2** - replicaset with livenessProbe, readinessProbe
- **etcd-minikube** – static pod; controller, namespace: kube-system, component: etcd, tier:control-plane, system-node-critical with livenessProbe, startupProbe
- **kindnet-ntrzd**, **kindnet-9gwvs** – DaemonSet kindnet
- **kube-apiserver-minikube** – static pod; controller, namespace: kube-system, component: kube-apiserver, tier:control-plane, system-node-critical with livenessProbe, readinessProbe, startupProbe
- **kube-controller-manager-minikube** – static pod; controller, namespace: kube-system, component: kube-controller-manager, tier:control-plane, system-node-critical with livenessProbe, startupProbe
- **kube-proxy-rcpl2**, **kube-proxy-s7582** – DaemonSet kube-proxy
- **kube-scheduler-minikube** – static pod; controller, namespace: kube-system, component: kube-scheduler, tier:control-plane, system-node-critical with livenessProbe, startupProbe

---

## веб-сервер
решил базировать на nginx, поскольку лучше всего понимаю как его быстро развернуть и настроить.

```
docker image build --tag gagafonov/kubernetes-intro-web:latest .
docker run --publish 127.0.0.1:8000:8000/tcp -it kubernetes-intro-web
lsof -i :8000
curl 127.0.0.1:8000
curl 127.0.0.1:8000/homework.html
docker image push gagafonov/kubernetes-intro-web:latest
```

## microservices-demo frontend
```
docker image build --tag gagafonov/microservices-demo:latest .
docker image push gagafonov/microservices-demo:latest
```

### error
```
main ~/learn-kube/microservices-demo/src/frontend> k logs frontend
{"message":"Tracing disabled.","severity":"info","timestamp":"2023-03-12T09:45:29.527996519Z"}
{"message":"Profiling disabled.","severity":"info","timestamp":"2023-03-12T09:45:29.528074676Z"}
panic: environment variable "PRODUCT_CATALOG_SERVICE_ADDR" not set

goroutine 1 [running]:
main.mustMapEnv(0xc000112540, {0xbfc8b5, 0x1c})
    /src/main.go:208 +0xb9
main.main()
    /src/main.go:124 +0x5be
```

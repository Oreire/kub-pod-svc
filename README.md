# kub-pod-svc


Key Details:
- **Grafana**: Exposed on NodePort `32000`, accessible at `<NodeIP>:32000`.
- **NGINX**: Exposed on NodePort `30001`, accessible at `<NodeIP>:30001`.
- **Prometheus**: Exposed on NodePort `32001`, accessible at `<NodeIP>:32001`.

Error: 

Run # Applying manifests to the Kubernetes cluster
E0312 13:25:42.518506    1804 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"http://localhost:8080/api?timeout=32s\": dial tcp [::1]:8080: connect: connection refused"
E0312 13:25:42.520245    1804 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"http://localhost:8080/api?timeout=32s\": dial tcp [::1]:8080: connect: connection refused"
unable to recognize "nginxpod.yaml": Get "http://localhost:8080/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
unable to recognize "nginxpod.yaml": Get "http://localhost:8080/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
Failed to apply nginxpod.yaml
E0312 13:25:42.559538    1811 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"http://localhost:8080/api?timeout=32s\": dial tcp [::1]:8080: connect: connection refused"
E0312 13:25:42.561356    1811 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"http://localhost:8080/api?timeout=32s\": dial tcp [::1]:8080: connect: connection refused"
unable to recognize "prometheuspod.yaml": Get "http://localhost:8080/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
unable to recognize "prometheuspod.yaml": Get "http://localhost:8080/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
Failed to apply prometheuspod.yaml
E0312 13:25:42.600940    1818 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"http://localhost:8080/api?timeout=32s\": dial tcp [::1]:8080: connect: connection refused"
E0312 13:25:42.602652    1818 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"http://localhost:8080/api?timeout=32s\": dial tcp [::1]:8080: connect: connection refused"
unable to recognize "grafanapod.yaml": Get "http://localhost:8080/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
unable to recognize "grafanapod.yaml": Get "http://localhost:8080/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
Failed to apply grafanapod.yaml






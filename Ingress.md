![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/888d84a8-2f56-490e-baaf-1bbb66634f5e)

![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/31e237ab-7584-4071-a2d5-366fda472899)


![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/79a7f9e0-d9a6-45af-8a4f-bc102e540046)


# Ingress
API Object in kubernetes
1. Expose HTTP and HTTPS Routes from outside the cluster
2. Path Based and Route Based Routing
3. Load Balancing and SSL Termination


```shell
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
spec:
  rules:
    - host: mycourses.com
      http:
        paths:
          - pathType: Prefix
            path: /
            backend:
              service:
                name: home-service
                port:
                  number: 8080
          - pathType: Prefix
            path: /courses
            backend:
              service:
                name: course-service
                port:
                  number: 8181
```

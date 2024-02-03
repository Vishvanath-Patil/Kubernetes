Video Ref:- https://youtu.be/-2VKSYffdYM?si=aEi7123QjZyTjGLn

![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/888d84a8-2f56-490e-baaf-1bbb66634f5e)

![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/31e237ab-7584-4071-a2d5-366fda472899)


![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/79a7f9e0-d9a6-45af-8a4f-bc102e540046)

## Path Based Routing :-
![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/67c66937-3d73-4cc5-a6b1-669d277dfe7a)

## Host Based Routing ( Sub-Domain Based Routing)
![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/154a833b-f504-4203-a144-27ef3d5381ea)

## SSL Termination
![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/dd4f4d70-224c-483f-92eb-b2836ed33fe1)

## Problem Without Ingress
![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/819467cc-e3fc-4637-9dee-c8f0f156689c)


# Ingress
API Object in kubernetes
1. Expose HTTP and HTTPS Routes from outside the cluster
2. Path Based and Route Based Routing
3. Load Balancing and SSL Termination

## Ingress Controller Types
Nginx Controller
HAProxy Ingress
Isto Ingrss

## Ingress Controller
![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/21c1c008-7698-4061-abe9-123a8a9acd14)

## Final Flow of Ingress 
![image](https://github.com/Vishvanath-Patil/Kubernetes/assets/130968991/250d712c-5949-427b-9986-95148bccb778)

## Ingress Resource File 
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

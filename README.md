# Save Sonam Wangchuk

A small static advocacy page, deployed with Argo CD and Kustomize.

## Deploy

Create an Argo CD Application pointing to this repository and set its path to `.`. Choose the destination cluster and namespace in the Application settings; this project deliberately does not hard-code a namespace. Argo CD detects `kustomization.yaml`, generates a ConfigMap from `index.html`, and mounts it into the nginx web server.

To apply it manually to the current kubectl context:

```sh
kubectl apply -k .
```

## Preview

After deployment, forward the Service to your machine:

```sh
kubectl port-forward service/save-sonam-wangchuk 8080:80
```

Then open <http://localhost:8080>. The Service is `ClusterIP`; connect it to your existing Ingress controller if you want a public URL.
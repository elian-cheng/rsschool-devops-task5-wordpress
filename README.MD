# WordPress and MySQL Helm Chart

This Helm Chart facilitates the deployment of WordPress in a dedicated namespace called `wordpress`, utilizing NodePort for external access. It automatically provisions the necessary Deployment, Service, and PersistentVolumeClaim resources for both WordPress and MySQL.

## Chart Components

- `Chart.yaml` — Contains Helm chart metadata.
- `values.yaml` — Main configuration file for WordPress and MySQL, specifying images, services, storage, and resource limits.
- `templates/namespace.yaml` — Defines the `wordpress` namespace.
- `templates/wp-deployment.yaml` — Deployment configuration for WordPress.
- `templates/wp-service.yaml` — NodePort Service configuration for WordPress.
- `templates/wp-pvc.yaml` — PersistentVolumeClaim for WordPress.
- `templates/mysql-deployment.yaml` — Deployment configuration for MySQL.
- `templates/mysql-service.yaml` — Service configuration for MySQL.
- `templates/mysql-pvc.yaml` — PersistentVolumeClaim for MySQL.

## Deployment Instructions

1. Deploy the Helm chart in the `wordpress` namespace:

```bash
helm install my-wordpress ./wordpress --namespace wordpress --create-namespace
```

2. Verify the deployment:

```bash
kubectl get all -n wordpress
```

## Managing Pods

### Viewing Pods

To list all pods in the `wordpress` namespace:

```bash
kubectl get pods -n wordpress
```

### Connecting to Pods

To access a WordPress pod:

```bash
kubectl exec -it <wordpress-pod-name> -n wordpress -- /bin/bash
```

To access a MySQL pod:

```bash
kubectl exec -it <postgresql-pod-name> -n wordpress -- /bin/bash
```

### Viewing Logs

To view logs for a WordPress pod:

```bash
kubectl logs <wordpress-pod-name> -n wordpress
```

To view logs for a MySQL pod:

```bash
kubectl logs <mysql-pod-name> -n wordpress
```

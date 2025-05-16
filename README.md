# Kubernetes Hackathon Submission

This repository contains the solution for **Part 3: Storage** and **Part 4: Ingress** of the Kubernetes Hackathon hosted on [kubernetes.courselabs.co](https://kubernetes.courselabs.co/hackathon/).

---

##  Part 3 - Storage

### Overview
- The `stock-api` application uses a local `/cache` directory for performance caching. This cache should survive Pod restarts.
- The `products-db` is replaced with a **replicated Postgres StatefulSet** using the image `widgetario/products-db:postgres-replicated`.
- Persistent volume claims are used for database data storage, and replication is configured using environment variables.

### Files
- `part-3/stock-api-deployment.yaml`: Adds an `emptyDir` volume for caching in the `stock-api` pod.
- `part-3/products-db-statefulset.yaml`: StatefulSet for primary and secondary Postgres with persistent volumes and replication setup.
- `part-3/products-db-headless-service.yaml`: A headless service to support direct communication with the database pods.

---

##  Part 4 - Ingress

### Overview
- A custom NGINX ingress controller is deployed.
- Ingress routes are defined for:
  - `widgetario.local` → Web frontend
  - `api.widgetario.local` → Products API backend

### Files
- `part-4/ingress-controller.yaml`: Deploys an ingress controller.
- `part-4/web-ingress.yaml`: Routes the web app to `http://widgetario.local`.
- `part-4/products-api-ingress.yaml`: Routes the products API to `http://api.widgetario.local`.

---



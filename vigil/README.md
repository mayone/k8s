# Vigil
- Deploy [Vigil](https://github.com/valeriansaliou/vigil) for microservices status monitoring.
- Use [kustomize](https://github.com/kubernetes-sigs/kustomize) to generate customized YAML files.

---

## Run

### Apply
```console
just a <FOLDER_WITH_KUSTOMIZATION>
```

### Example: Apply staging
```console
just a overlays/staging
```

---

## Check deployment
```console
kubectl get pods
kubectl get configMap
```

---

## Forward and view

### Forward service
```console
just f
```

### View
- Go to http://localhost:8080/

---

## Delete

### Delete
```console
just d <FOLDER_WITH_KUSTOMIZATION>
```

### Example: Delete staging
```console
just d overlays/staging
```
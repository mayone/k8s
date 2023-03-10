# Vigil
- Deploy [Vigil](https://github.com/valeriansaliou/vigil) for microservices status monitoring.
- Use [kustomize](https://github.com/kubernetes-sigs/kustomize) to generate customized YAML files.

---

## Run

```sh
just a <KUSTOMIZATION_DIR>

# Ex. apply staging
just a overlays/staging
```

---

## View deployment

```sh
just v <KUSTOMIZATION_DIR>

# Ex. view staging
just v overlays/staging
```

---

## Forward and view

### Forward service

```sh
just f
```

### View
- Go to http://localhost:8080/

---

## Delete

```sh
just d <KUSTOMIZATION_DIR>

# Ex. delete staging
just d overlays/staging
```

## Rollout (Example)

### Rollout
```sh
# Ex. Rollout by set image version to 1.25.0
kubectl set image deploy/vigil vigil=valeriansaliou/vigil:v1.25.0 --record

# Check rollout history
kubectl rollout history deploy vigil

# Check deployment image version
kubectl describe deploy vigil | grep Image:
```

### Rollback
```sh
# Check rollout history
kubectl rollout history deploy vigil

# Ex. Rollback to specified revision
kubectl rollout undo deploy vigil --to-revision=1

# Check deployment image version
kubectl describe deploy vigil | grep Image:
```

---

## Appendix

### Compare staging with production

```sh
diff \
    <(kubectl kustomize overlays/staging) \
    <(kubectl kustomize overlays/production) |\
    more
```

## References

- [Declarative Management of Kubernetes Objects Using Kustomize](https://kubernetes.io/docs/tasks/manage-kubernetes-objects/kustomization/)
# Release Note 🍻

EMQX Operator 2.2.8 has been released.

## Supported version
+ apps.emqx.io/v2beta1

  + EMQX at 5.1.1 and later
  + EMQX Enterprise at 5.1.1 and later

+ apps.emqx.io/v1beta4

  + EMQX at 4.4.14 and later
  + EMQX Enterprise at 4.4.14 and later

## Fixes 🛠

+ `apps.emqx.io/v2beta1 EMQX`.

  + Fix sometimes the EMQX operator controller will update K8s service, even the service is not changed

  + Fix sometimes the EMQX operator controller will access the reload config API of EMQX, even if the config is not changed

## How to install/upgrade EMQX Operator 💡

> Need make sure the [cert-manager](https://cert-manager.io/) is ready

```
helm repo add emqx https://repos.emqx.io/charts
helm repo update
helm upgrade --install emqx-operator emqx/emqx-operator \
  --namespace emqx-operator-system \
  --create-namespace \
  --version 2.2.8
kubectl wait --for=condition=Ready pods -l "control-plane=controller-manager" -n emqx-operator-system
```

## Warning 🚨
`apps.emqx.io/v1beta3` and `apps.emqx.io/v2alpha1` will be dropped soon

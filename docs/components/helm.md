# Helm

[Helm] is a package manager for Kubernetes and can be used to install workloads
in a cluster.

## Installation

[Helm Client] is required to install Helm Server — [Tiller] into a cluster and
for any further Helm based operations.

For Helm (actually Tiller) to be able doing operations across the cluster
we increase its privileges by using the "cluster-admin" cluster role. For that
we use the [RBAC Tiller Manifest] to create an appropriate service account and
the corresponding role binding:

```
$ kubectl apply -f https://raw.githubusercontent.com/travelping/cennsonic/master/components/helm/tiller-rbac.yaml
```

After that we can install Helm in a way to use that service account:

```
$ helm init --service-account tiller
```

<!-- Links -->

[Helm]: https://helm.sh
[Tiller]: https://docs.helm.sh/using_helm/#installing-tiller
[Helm Client]: https://docs.helm.sh/using_helm/#installing-the-helm-client
[RBAC Tiller Manifest]: ../../components/helm/tiller-rbac.yaml

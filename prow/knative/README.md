## Knative prow

This directory contains prow configs hosted for Knative. This prow is bumped by
[`bump.sh`](../bump.sh) script

### Prow Clusters

- [Prow control plane cluster(default prow cluster)](https://pantheon.corp.google.com/kubernetes/clusters/details/us-central1-f/prow?project=knative-tests)
  - Prow deployments, core configs, and plugins are hosted in this repo
  - Prow job configs are hosted in knative/test-infra repo
- [Build cluster](https://pantheon.corp.google.com/kubernetes/clusters/details/us-central1-f/knative-prow-build-cluster)
  - Build cluster deployments are hosted in this repo
  - Boskos resources are hosted in knative/test-infra repo
- [Trusted cluster](https://pantheon.corp.google.com/kubernetes/clusters/details/us-central1-a/prow-trusted)
  - This is a very basic cluster with important secrets

### Manually Deploy

Manual deployments are defined as in [Makefile](./Makefile), specifically:

- `make -C prow/knative deploy`: deploys all yamls under [cluster](./cluster)
- `make -C prow/knative deploy-build`: deploys all yamls under [cluster/build](./cluster/build)

## Prow Secrets

Some of the prow secrets are managed by kubernetes external secrets, which
allows prow cluster creating secrets based on values from google secret manager
(Not necessarily the same GCP project where prow is located). See more detailed
instruction at [Prow Secret](https://github.com/kubernetes/test-infra/blob/master/prow/prow_secrets.md).

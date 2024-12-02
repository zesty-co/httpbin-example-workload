# Httpbin Example Workload

This is an example workload that serves HTTP requests using httpbin and periodically simulates stress traffic.

## Prerequisites

- [Git](https://git-scm.com/)
- [Helm](https://helm.sh/)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)

## Preparation

- Make sure that you are connected to the correct Kubernetes cluster:
```bash
kubectl config current-context
```

You should see the name of the cluster you want to install the workload on.

## Installation

1. Clone the repository
```bash
git clone git@github.com:zesty-co/httpbin-example-workload.git
```

2. Navigate to the directory
```bash
cd httpbin-example-workload
```


3. Install the helm chart
```bash
helm upgrade zesty-httpbin-example ./ --install --namespace zesty-examples --create-namespace --values values.yaml
```

## Manual trigger

The stress test runs periodically once a week by default, but in case you want to manually trigger the stress traffic, you can manually run the job:
```bash
 kubectl create job --namespace zesty-examples --from=cronjob/stress-test run-stress
```

## Uninstalling

- To remove the example workload, run the following command:
```sh
helm delete zesty-httpbin-example --namespace zesty-examples
```

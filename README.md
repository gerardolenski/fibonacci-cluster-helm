# Fibonacci cluster - helm charts

This is the helm chart for the Kubernetes. For more description see the
repository: [fibonacci-cluster-k8s](https://github.com/gerardolenski/fibonacci-cluster-k8s)

## infra v1.0.0

The `infra` directory contains charts for infrastructure services:

- Artemis v2.37.0
- pgAdmin v8.4
- PostgreSQL v16.4
- Redis v7.4.1

They can be installed by command:

```
$ helm instal -f values-infra.yml infra infra/
```

The minimum content of custom `values-infra.yml` file are necessary passwords (Base64 encoded):

```
postgres:
  config:
    POSTGRES_PASSWORD: "base64 secret"
pgadmin:
  config:
    PGADMIN_DEFAULT_PASSWORD: "base64 secret"
artemis:
  config:
    ARTEMIS_PASSWORD: "base64 secret"
```

## fib v1.0.0

The `fib` directory contains charts for Fibonacci applications:

- Front App v2.0.0
- Task Manager v2.0.0
- Message Relay v1.0.0
- Fibonacci Worker v2.0.0
```
$ helm install -f values-fib.yaml fib fib/
```

The minimum content of custom `values-fib.yml` file are necessary passwords (Base64 encoded):

```
global:
  infra:
    broker:
      password: "base64 secret"
    postgres:
      password: "base64 secret"
```
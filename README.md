# OpenShift Day-2 Configuration Tool

The OpenShift Day-2 Configuration Tool is a tool to configure Day-2 environment on a running OpenShift Cluster.

## Supported configurators
- LDAP
- Ingress
- Nodes

*ETCD, MachineConfig operator and Infra/Worker nodes tasks configurators are to be added in the future.*

## How to use

### Setup
- OpenShift cluster must be provisioned and running.
- Cluster admin privileges are required.
- [bitnami-labs SealedSecrets](https://github.com/bitnami-labs/sealed-secrets) custom resource must be installed.
- [butane](https://github.com/coreos/butane/tree/main) CLI tool must be installed.

### Configuration
- Edit [day2 config](day2_configuration.example.yaml) file; replace all placeholders with values.
- Set `kubeconfig` to point to the cluster's kubeconfig file.
- Unset `KUBECONFIG` environment variable.

```bash
unset KUBECONFIG
```

## Run the tool

```bash
poetry install
poetry run python openshift_day2_configurator/cli.py -c <path to config file>
```

To run in debug mode, add `--verbose` or `-v` to the command.  
To drop to `ipdb` shell on exception, add `-pdb` to the command.

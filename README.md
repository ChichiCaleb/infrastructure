
## Introduction

> - **Modular and Extensible Infrastructure Setup with Seamless Data Exchange Between Terraform and Kubernetes**

> - **Serves as infrastructure repo used in testing `alustan` platform orchestrator**


## Architecture

The project architecture consists of the following main components:

- **Cluster**: current implementaion `EKS` : Users are free to add other managed kubernetes.

- **Database**: Current implementation `AWS RDS`: Users are free to add other DB implementations

- **Gitops Bridge**: Shares cloud matadata with kubernetes resources/manifest using argocd cluster secret.

- **Remote Backend**: Remote backend with `S3` and `Dynamodb` with a single flow deploy script.

- **Project is modular and extensible**


## setup

- Run `make setup` to install and configure all needed dependencies. 

- Run `make store-secrets` to create or store secret in aws secret manager

- Run `make deploy` to bootstrap a control cluster with other infrastructure

- Run `make retrieve-creds` to retrieve relevant credentials and urls

- Run `make destroy` to destroy the control cluster with other infrastructure

- Run `make destroy-cluster` to destroy the control cluster

- Run `make destroy-db` to destroy bootstrapped database

- Run `make build-deploy` to build a deploy binary from the go deploy code

- Run `make build-destroy` to build a destroy binary from the go destroy code

- To see all available options run `make help`

- **All needed variables can be found in root level variables.tf**

## Relevant URLs

- **argocd UI:** `argocd.<workspace>.<domain>`

- **Grafana UI:** `grafana.<workspace>.<domain>`

- **Prometheus UI:** `prometheus.<workspace>.<domain>`

- **Kubecost UI:** `kubecost.<workspace>.<domain>`

- **Argo rollout Dashboard:** `kubectl argo rollouts dashboard -n <namespace>`; Then visit `localhost:3100`

- **Robusta UI:** [robusta](https://home.robusta.dev/)

## Relevant Secrets Keys to be stored in aws secret manager

- `SSH_KEY`: git ssh key (if using private repo)

- `SLACK_API_KEY`: slack api key (if robusta is enabled)
- `ROBUSTA_SINK_TOKEN`: robusta sink token (if robusta is enabled)
- `ROBUSTA_ACCOUNT_ID`: robusta account id (if robusta is enabled)
- `ROBUSTA_SIGNING_KEY`: robusta signing key (if robusta is enabled)

- `DB_NAME`: database name (if provision DB)
- `DB_USER`: database user (if provision DB)
- `DB_PASSWORD`: database password (if provision DB)



**Alustan:** focuses on building tools and platforms that ensures right implementation of devops principles


![wakapi badge](https://wakapi.simulatan.me/api/badge/SIMULATAN/interval:any/label:Kubernetes?label=Time%20Spent)

# Kubernetes Configs
This repo contains the kubernetes configurations for my projects. The exact files from this repo are deployed automatically using [ArgoCD](https://argoproj.github.io/cd/).

Feel free to take a look around and use anything you find useful (see [LICENSE](./LICENSE)). If you have any questions, feel free to ask. I'm always happy to help.

As for the contained applications; most notably, I set up [Authelia](auth/authelia) for SSO and 2FA, and [Wakapi](wakapi) to track my coding activity. Both are highly available and will be deployed to multiple nodes to ensure uptime.

## Applications
The list of applications includes, but is not limited to:
- [Authelia](auth/authelia)
  - provides SSO for my services
  - exposes OIDC provider
  - also provides 2FA
- [OpenLDAP](auth/ldap)
  - stores the SSO users + groups
- [ArgoCD](argocd)
  - deploys the configs in this repo
  - used for 99% of the deployed resources
  - avoid applying outside of ArgoCD if possible!
- [Cert-Manager](cert-manager)
  - creates and manages LetsEncrypt certificates for my domains
- [Postgres-Operator](postgres-operator)
  - eases the management of postgres instances
  - `kind: postgresql` indicates that the instance is managed by this operator
  - as such, it is needed to create some of the clusters used by other applications
- [Sealed-Secrets](sealed-secrets)
  - this allows me to store secrets in this git repo
- [Wakapi](wakapi)
  - tracks my coding activity (see badge above)
- [kube-arch-scheduler](kube-arch-scheduler)
  - used to avoid scheduling pods on nodes with different architectures
  - pretty much unused at the moment as oracle yeeted my ARM instance

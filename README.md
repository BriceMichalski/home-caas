# Home

Ansible project for my home servers installation and configuration

## Playbook

- `playbook/infrastructure.yml`: it allows the configuration and deployment of my home kubernetes cluster.
- `playbook/applications.yml`: deploy all my apps on kubernetes cluster

## Use

Install requirements:

```bash
ansible-galaxy install -r requirements.yml
```

Launch playbook:

```bash
ansible-playbook --inventory inventories/prod/hosts playbook/infrastructure.yml --vault-pass-file ./pwd.vault
ansible-playbook --inventory inventories/prod/hosts playbook/applications.yml --vault-pass-file ./pwd.vault
```

To run only a part of the playbook, see the tag list.

## Tags list

> Not in execution order

|Tag Name| Usage |
|---|---|
| **hardening** | Configuration and customization of my server before installing kubernetes |
| **hardening::disk** | Part of **hardening** : mount and prepare my external hard drives |
| **hardening::swap** | Part of **hardening**: disable swap (kubernetes prerequisite) |
| **hardening::timezone** | Part of **hardening**: set the timezone to Europe/Paris |
| **hardening::upgrade** | Part of **hardening**: Updating packages and removing unnecessary ones |
| **hardening::usual** | Part of **hardening**: Installing utilities that I frequently use |
| **hardening::usual::package** | Part of **hardening::usual**: Installing k9s (kubernetes cli tools) |
| **kubernetes** | Installation and configuration of the kubernetes (single-node) cluster, deployment of hosted applications |
| **kubernetes::cert-manager** | Part of **kubernetes** : installation of cert-manager with letsencrypt acme and the dns01 cloudflare challenge for end-to-end encryption|
| **kubernetes::cluster** | Part of **kubernetes** : Installation of docker and the kubernetes cluster itself |
| **kubernetes::k9s** | Part of **kubernetes**: Installing k9s (kubernetes cli tools) |
| **kubernetes::external-dns** | Part of **kubernetes**: Configuring `external-dns` tool for dynamic declaration of hosted application dns |
| **kubernetes::ingress-controller** | Part of **kubernetes**: Installation of an ingress controller (`nginx`) for application exposure outside the cluster |
| **kubernetes::metallb** | Part of **kubernetes**: Installation of `metallb`, a load-balancer implementation for bare metal Kubernetes clusters, using standard routing protocols. |
| **kubernetes::volumes** | Part of **kubernetes**: Creation of local persistent volumes for the provision of disk space to hosted applications |
| **kubernetes::apps** | Part of **kubernetes**: Hosted Application Deployment |

## Home server spécification

My home server is a mini pc bought on amazon : [amazon link](https://www.amazon.fr/gp/product/B0919ZGR1R)

| |  |
|---|---|
| CPU | Intel Core I5-8279U - 4 Cores /  8 Threads |
| GPU | Intel Iris Plus Graphics 655 |
| Memory | 16Gb DDR4 - 2 x 8Gb |
| OS | Ubuntu 20.04.3 LTS x86_64 |

## Domain

- michalski.fr
- mbcaas.com
- on-mange-quoi.com

Managed by [cloudflare](https://www.cloudflare.com/).

## Usefull link

- [Nginx Ingress controller](https://kubernetes.github.io/ingress-nginx/)
- [Nginx ingress controller - baremetal considerations](https://kubernetes.github.io/ingress-nginx/deploy/baremetal/)
- [Metallb installation](https://metallb.universe.tf/installation/)
- [External-dns](https://github.com/kubernetes-sigs/external-dns)
- [External-dns with Cloudflare](https://github.com/kubernetes-sigs/external-dns/blob/master/docs/tutorials/cloudflare.md)
- [Cloudflare token generation](https://support.cloudflare.com/hc/fr-fr/articles/200167836-Gestion-des-jetons-et-cl%C3%A9s-de-l-API#12345680)
- [Force External-dns to target my internet box public IP](https://github.com/kubernetes-sigs/external-dns/blob/master/docs/faq.md#are-other-ingress-controllers-supported)
- [Cert Manager install](https://cert-manager.io/docs/installation/)
- [Cert Manager LetsEncrypt ACME](https://cert-manager.io/docs/configuration/acme/)
- [Cert Manager DNS01 Challenge with cloudflare](https://cert-manager.io/docs/configuration/acme/dns01/cloudflare/)

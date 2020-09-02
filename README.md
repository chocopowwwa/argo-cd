你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。

# Argo CD - Declarative Continuous Delivery for Kubernetes

## What is Argo CD?

Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes.

![Argo CD UI](docs/argocd-ui.gif)

## Why Argo CD?

Application definitions, configurations, and environments should be declarative and version controlled.
Application deployment and lifecycle management should be automated, auditable, and easy to understand.

## Getting Started

Follow our [getting started guide](docs/getting_started.md). Further [documentation](docs/)
is provided for additional features.

## How it works

Argo CD follows the **GitOps** pattern of using git repositories as the source of truth for defining
the desired application state. Kubernetes manifests can be specified in several ways:
* [ksonnet](https://ksonnet.io) applications
* [helm](https://helm.sh) charts
* Simple directory of YAML/json manifests

Argo CD automates the deployment of the desired application states in the specified target environments.
Application deployments can track updates to branches, tags, or pinned to a specific version of 
manifests at a git commit. See [tracking strategies](docs/tracking_strategies.md) for additional
details about the different tracking strategies available.

## Architecture

![Argo CD Architecture](docs/argocd_architecture.png)

Argo CD is implemented as a kubernetes controller which continuously monitors running applications
and compares the current, live state against the desired target state (as specified in the git repo).
A deployed application whose live state deviates from the target state is considered `OutOfSync`.
Argo CD reports & visualizes the differences, while providing facilities to automatically or
manually sync the live state back to the desired target state. Any modifications made to the desired
target state in the git repo can be automatically applied and reflected in the specified target
environments.

For additional details, see [architecture overview](docs/architecture.md).

## Features

* Automated deployment of applications to specified target environments
* Continuous monitoring of deployed applications
* Automated or manual syncing of applications to its desired state
* Web and CLI based visualization of applications and differences between live vs. desired state
* Rollback/Roll-anywhere to any application state committed in the git repository
* Health assessment statuses on all components of the application
* SSO Integration (OIDC, OAuth2, LDAP, SAML 2.0, GitLab, Microsoft, LinkedIn)
* Webhook Integration (GitHub, BitBucket, GitLab)
* PreSync, Sync, PostSync hooks to support complex application rollouts (e.g.blue/green & canary upgrades)
* Audit trails for application events and API calls
* Parameter overrides for overriding ksonnet/helm parameters in git

## Development Status
* Argo CD is being used in production to deploy SaaS services at Intuit

## Roadmap
* Auto-sync toggle to directly apply git state changes to live state
* Service account/access key management for CI pipelines
* Support for additional config management tools (Kustomize?)
* Revamped UI, and feature parity with CLI
* Customizable application actions

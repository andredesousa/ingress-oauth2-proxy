# OAuth2 Proxy with Ingress

This project shows how to use [OAuth2 Proxy](https://oauth2-proxy.github.io/oauth2-proxy/), [GitHub OAuth Apps](https://github.com/settings/developers) and [NGINX Ingress Controller](https://kubernetes.github.io/ingress-nginx/) to route traffic.

## Overview

Many application do not provide built-in authentication or access control out-of-the-box.
Due to the sensitive data these applications process, this can be a major problem and it is often necessary to provide some type of security.

[OAuth2 Proxy](https://oauth2-proxy.github.io/oauth2-proxy/) is a reverse proxy that sits in front of your application and handles the complexities of OpenID Connect/OAuth 2.0 for you.

<img src="https://developer.okta.com/assets-jekyll/blog/add-auth-to-any-app-with-oauth2-proxy/oauth2-proxy-diagram-09c03e3355965bf4d0f8d26911206e015d448b8802f86237a8a17701c173d04e.jpg" width=35% height=35%>

OAuth2 Proxy provides authentication using providers (GitHub, Google, and others) to validate accounts by email, domain or group.

## Prerequisites

Follow the next instructions to configure and run the project on your local machine:

- Install, at least, [Helm](https://helm.sh/), [minikube](https://minikube.sigs.k8s.io/) and [Docker](https://www.docker.com/).
- Install required charts with `helm dependency update` command.
- Register a new *GitHub App* to allow the access to *GitHub OAuth Apps*.
- Replace the following variables in the [values.yaml](values.yaml) file:
  - `OAUTH2_PROXY_CLIENT_ID`
  - `OAUTH2_PROXY_CLIENT_SECRET`
  - `OAUTH2_PROXY_COOKIE_SECRET`
  - `OAUTH2_PROXY_DOMAIN`

## GitHub OAuth Apps

Before you begin, you’ll need a free GitHub developer account.
Go to <https://github.com/settings/developers> and register a new OAuth application.

## Deploying

You can deploy to your cluster using `helm install [chart-name] [chart-folder-name]` command.
Replacing the missing values, the command is:

```bash
helm install oauth2-demo .
```

If you want to uninstall use `helm uninstall oauth2-demo` command.

The `helm list` command list all releases in your cluster.
To see the status of your release use `helm status [release-name]` command.

## References

For further reference, please consider the following articles:

- [Helm Commands](https://helm.sh/docs/helm/)
- [OAuth2 Proxy Docs](https://oauth2-proxy.github.io/oauth2-proxy/docs/)
- [External OAUTH Authentication](https://kubernetes.github.io/ingress-nginx/examples/auth/oauth-external-auth/)
- [Add Auth to any App with OAuth2 Proxy](https://developer.okta.com/blog/2022/07/14/add-auth-to-any-app-with-oauth2-proxy#is-oauth2-proxy-right-for-your-application)

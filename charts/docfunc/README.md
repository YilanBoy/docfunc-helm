# DocFunc Helm Chart

This is a Helm chart for deploying my blog - DocFunc.

The blog source code is [here](https://github.com/YilanBoy/blog).

## Sealed Secrets

Because I use Argo CD to deploy my blog, I use [Sealed Secrets](https://github.com/bitnami-labs/sealed-secrets) to encrypt the secrets.

To encrypt & decrypt the secrets, you need to install the Sealed Secrets controller first.

```bash
helm repo add sealed-secrets https://bitnami-labs.github.io/sealed-secrets
helm install sealed-secrets -n kube-system --set-string fullnameOverride=sealed-secrets-controller sealed-secrets/sealed-secrets
```

Then you can use `kubeseal` to encrypt the secrets.

> [!NOTE]
>
> You need to install `kubeseal` first.

```bash
kubeseal -f mysecret.yaml -w mysealedsecret.yaml
```

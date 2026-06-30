# gh-oc-testing

GitHub Action to log in to OpenShift using a short-lived token via the Kubernetes TokenRequest API. Captures a pcap for debugging connection issues.

## Inputs

| Input | Required | Default | Description |
|---|---|---|---|
| `oc-server` | yes | | OpenShift server URL |
| `oc-token` | yes | | Long-lived service account token |
| `oc-namespace` | yes | | Namespace of the service account |
| `oc-service-account` | no | `ghactions` | Service account name |

## Usage

```yaml
- uses: bcgov/gh-oc-testing@main
  with:
    oc-server: ${{ vars.OC_SERVER }}
    oc-token: ${{ secrets.OC_TOKEN }}
    oc-namespace: ${{ vars.OC_NAMESPACE }}
```

## Trigger manually

Requires `OC_TOKEN` set as a repo secret.

```sh
gh workflow run oc-login.yml --repo bcgov/gh-oc-testing \
  -f oc-server=https://your-server:6443 \
  -f oc-namespace=your-namespace
```

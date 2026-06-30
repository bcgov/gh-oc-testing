# gh-oc-testing

Manually triggered workflow to test OpenShift login from GitHub Actions. Captures a pcap for debugging network/timeout issues.

## Setup

Add `OC_TOKEN` as a repo secret — a long-lived service account token for the `ghactions` SA.

## Trigger

```sh
gh workflow run oc-login.yml --repo bcgov/gh-oc-testing \
  -f oc-server=https://api.silver.devops.gov.bc.ca:6443 \
  -f oc-namespace=e1e498-prod
```

## Outputs

Each run uploads an `oc-login-pcap` artifact containing a packet capture of the connection to the OpenShift API server, retained for 3 days.

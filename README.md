# Deep Security Agent — OpenShift Helm Chart

This Helm chart deploys the [Trend Micro Deep Security Agent](https://www.trendmicro.com/en_us/business/products/hybrid-cloud/cloud-one-workload-security.html) as a DaemonSet on Red Hat OpenShift clusters. The agent runs on every node and provides real-time anti-malware protection for both host file systems and running containers.

## What It Does

The Deep Security Agent connects to your Deep Security Manager (DSM) and:

- Scans host file systems and containers for malware in real time
- Reports protection status back to the DSM
- Uses Trend Micro's Smart Protection Network for up-to-date threat intelligence
- Helps meet continuous compliance requirements

## Installation

### Add the Helm repository

```bash
helm repo add ds-agent https://trendmicro.github.io/dsao/
helm repo update
```

### Install the chart

```bash
helm install ds-agent ds-agent/ds-agent \
  --namespace openshift \
  --set dsmUrl=<your-dsm-url>
```

Replace `<your-dsm-url>` with the URL of your Deep Security Manager (for example, `https://dsm.example.com:4119`).

## Useful Commands

```bash
# Upgrade after a values change
helm upgrade ds-agent charts/dsao --namespace openshift --set dsmUrl=<url>

# Uninstall
helm uninstall ds-agent --namespace openshift
```

## Resources

- [Trend Micro Cloud One Workload Security — OpenShift](https://docs.trendmicro.com/en-us/documentation/article/trend-micro-cloud-one-workload-security-openshift)
- [Agent installation on Red Hat OpenShift](https://docs.trendmicro.com/en-us/documentation/article/trend-micro-cloud-one-workload-security-agent-install#install-agent-rh-openshift)

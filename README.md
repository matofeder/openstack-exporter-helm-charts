# Helm Chart for OpenStack Exporter

## Description

This is the official Helm Chart for [OpenStack Exporter](https://github.com/openstack-exporter/openstack-exporter), a tool to export Prometheus metrics from a running OpenStack Cloud.

## Configuration

The chart configuration is done in the `values.yaml` file.

## Usage

### Installation from helm repository
```bash
# Add openstack-exporter helm repository
helm repo add openstack-exporter https://openstack-exporter.github.io/helm-charts
helm repo update
# Fetch the available charts and versions
helm search repo openstack-exporter --versions

# Get the latest prometheus-openstack-exporter chart version (requires `jq`) & install it
version="$(helm search repo openstack-exporter -ojson | jq -r '.[0].version')"
helm install prometheus-openstack-exporter openstack-exporter/prometheus-openstack-exporter --version $version
```
### Installation from source
```bash
# Get a local copy
git clone https://github.com/openstack-exporter/helm-charts.git

# Package the chart
cd helm-charts/charts/prometheus-openstack-exporter/
helm package . 

# Get chart version & install
version="$(awk '/^version:/{ print $NF }' Chart.yaml)"
helm install prometheus-openstack-exporter prometheus-openstack-exporter-${version}.tgz
```

## Contributing

Please fill pull requests or issues under Github.

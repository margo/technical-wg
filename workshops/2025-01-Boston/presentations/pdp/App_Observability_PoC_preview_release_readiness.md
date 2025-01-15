# Application Observability PoC Preview Release Readiness

It might make sense to use some, or all, of the existing [application observability prototype](https://github.com/margo/app-observability-wg/tree/main/research-prototype) as a starting point for the preview release reference implementation.

## Publishing Application Observability Data

See [specification](https://specification.margo.org/app-interoperability/publishing-application-observability-data/) for additional details

1. We have a [basic application](https://github.com/margo/app-observability-wg/tree/pdp/simple-otel-app/otel-app) that emits logs, metrics and traces
2. The ability deploy this as an Margo application on docker or kubernetes has not been implemented.
3. It's not setup to use the environment variables that should be injected by the Margo device as [defined here](https://specification.margo.org/device-interoperability/collecting-application-observability-data/#connecting-to-the-opentelemetry-collector)

## Collecting Application Observability Data

See [specification](https://specification.margo.org/device-interoperability/collecting-application-observability-data/) for additional details

1. We have scripts to install and configure the [OTEL Collector](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main) on a single and multi-node Kubernetes device
    - These manifests aren't as portable as they would need to be and would need to be updated to make things more configurable when deploying in different environments.
    - These scripts have only been tried with K3s
2. We have a docker-compose file that configures and runs the OTEL Collector on a standalone (docker and podman) device.
3. The OTEL Collector has configuration to emit all [default metrics](https://specification.margo.org/device-interoperability/collecting-application-observability-data/#application-observability-default-telemetry) defined in the specification.
4. The PoC does not have anything implemented to inject the [required environment variables](https://specification.margo.org/device-interoperability/collecting-application-observability-data/#connecting-to-the-opentelemetry-collector) into the containers

## Consuming Application Observability Data

See [specification](https://specification.margo.org/orchestration/workload/consuming-application-observability-data/) for additional details

1. We have scripts to install the OTEL Collector, Prometheus (metrics), Loki (logs), and Grafana (visualization) using kubernetes manifests.
    - These manifests aren't as portable as they would need to be and would need to be updated to make things more configurable when deploying in different environments.
    - These scripts have only been tried with K3s
    - We should probably change the use of Loki for OpenSearch because of potential licensing concerns
2. The OTEL Collector is configured to allow receiving telemetry from other OTEL Collectors using basic authentication
3. There is currently nothing being deployed for traces so we'd need to add something like Jaeger.
4. There is are no default Grafana visualizations

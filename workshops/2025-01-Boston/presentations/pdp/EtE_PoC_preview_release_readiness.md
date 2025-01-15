# End-to-End POC Preview Release 1 Readiness Status

It might make sense to use some, or all, of the existing [end-to-end prototype](https://github.com/margo/End-To-End-Prototypes/tree/pdp/go-prorotype) as a starting point for the preview release reference implementation.

The following information indicates the readiness status for the end-to-end prototype compared to the requirements defined for the preview release.

- The PoC is written in Go
- The PoC has basic functionality for the WoS and the WoA for a kubernetes devices
- The PoC only stores data in memory (apart from the ApplicationDescription and ApplicationDeployment in Git)
- The PoC has no security or concept of tenants
- The PoC uses [Gogs](https://gogs.io/) for a local Git repository
- The PoC still uses Git for communicating the desired state (ApplicationDeployment) to the device
- The PoC is my first time using Go so code quality could be an issue
- The PoC doesn't have any tests implemented, since it was a PoC

## Margo Preview Release 1 Scope: Application Management Scope

See [Issue](https://github.com/margo/specification/issues/43) for additional details

### Packaging Applications

1. It is possible for an application Vendor to package their OCI container-based application using either helm or docker compose profiles

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    |Defining one, or more, Helm charts to deploy to devices running Kubernetes | Y |  |
    |Defining one, or more, Docker compose packages to deploy to devices not running Kubernetes (e.g., Docker, Podman) | Partially | The WoS can handle docker-compose but there isn't a docker-compose device implementation |

2. It is possible to describe an application using the Application Description file format defined in the Margo specification. The Application Description format allows for defining the following:

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    | Identifying information about the application such as the name, version and description | Y | |
    | Application metadata to facilitate the ability for a workload orchestration vendor to display the application to the end-user so they can see what applications are available. This includes information such as: An application's icon, tagline, release notes, etc, Information about the application's author Information about the organization distributing the application | Y | See #3 below |
    | The ability to define how the application can be deployed by defining one, or more, deployment profiles | Y | |
    | The ability to request configuration input from the end-user to be used when deploying the application | Y | These can be defined and imported but the UI just shows textboxes |
    | The ability to provide information about how to validate configuration input values from the end-user before deploying the application | Y | These can be defined and imported but the UI doesn't do validation |

3. It is possible to provide the metadata artifacts (license file, release node, application icon, etc.) alongside the application definition file (margo.yaml) for the workload orchestration vendor to import along with the application definition file.

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    | Handle artifacts | N |  |

### Publishing Applications

| Requirement | Met By PoC | Comments |
|-------------|------------|----------|
| It is possible for a single git repository to contain one, or more, application packages. | Partially | The PoC only handles one application per repo but can support multiple repos |
| It is possible for the workload orchestration vendor's solution to pull in the application packages using the repository URL and branch name provided by the end user | Y | |

### Artifact Hosting

| Requirement | Met By PoC | Comments |
|-------------|------------|----------|
| It is possible for a device to a deploy a Kubernetes application by pulling down the helm chart and OCI container images from the registry without modifying the container registry location in the Helm chart. | Y | This is device/kubernetes configuration and not part of the PoC |
| It is possible for a device to deploy a Docker-Compose based application by pulling down the docker-compose package and OCI container images from the OCI registry without modifying the container registry location in the docker-compose file. | N | The PoC doesn't have docker-compose support |

### Application Observability

| Requirement | Met By PoC | Comments |
|-------------|------------|----------|
| It is possible for the application containers to connect to the OTEL collector using the OTEL environment variables injected into the container as defined in the Margo specification | N | The PoC has no application observability components |

## Margo Preview Release 1 Scope: Workload Management Interface

See [issue](https://github.com/margo/specification/issues/45) for additional details

1. The ability for the workload orchestration service to provide deployment specification(s) that follow the Margo standard

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    | Deploy one to many workloads | Y | |
    | Delete one to many existing workloads | Partially | Deleting works but not by evaluating desired state. It happens if you run a kubectl command to delete the desired state CRD |
    | Update workload(s) to a newer version of source code(container) | N |  |
    | Reconfigure currently running workload(s) via parameters | N |  |

2. The ability to build a Workload Orchestration Management service for orchestrating workloads to Margo compliant devices.

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    | Receive the workload deployment status update | N | |
    | Receive device capabilities | Y | The URL it's using needs to be changed to match the specification |
    | Deployment specification storage via Git | Y |  |
    | Deployment specification retrieval via Git | Y |  |

3. Device Workload Management Interface

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    | Send the workload deployment status updates as defined in the current specification | N | |
    | Send device capability information as defined in the current specification | N | |
    | Retrieve deployment specification associated with the device from Git | Y |  |
    | Configure a polling schedule | Y |  |

## Margo Preview Release 1 Scope: Device Requirements - Enable Margo Workloads

See [issue](https://github.com/margo/specification/issues/44) for additional details

### Device Requirements Scope - Enable Margo Workloads

1. The ability to build a Margo compliant device that fits one of the described roles

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    | Standalone Cluster (single-node cluster) | Y | The PoC has only been tested on K3s for WoS and WoA so there could be portability issues |
    | Standalone device | N |  |

2. The ability to host Margo compliant workloads via OCI container runtime

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    | Use OCI container runtime | Y | |

3. The ability to host the Margo management interface service(s) that enable workload deployment and maintenance

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    | Interpret deployment specification provided via the workload orchestrator. Subsequently deploy the described workloads on the local container runtime. | Partially | Helm charts only |
    | Provide workload deployment status updates to the workload orchestrator | N | |
    | Provide device capabilities information to the workload orchestrator. | Y | |

4. The ability to provide Margo compliant workloads an observability interface and collector to consolidate metrics, traces, and logs

    | Requirement | Met By PoC | Comments |
    |-------------|------------|----------|
    | OTEL Collector deployed and running on device | N | |
    | OTEL Collector configured to collect the required runtime observability data as stated in the specification. | N | |
    | Device is able to inject the required environment variables indicated in the specification into the locally hosted workloads | N | |

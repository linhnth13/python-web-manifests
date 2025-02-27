# python-web-manifests
Contains Kubernetes manifests and ArgoCD configuration files for deploying your application
# README for Python Web Manifests

This project contains Kubernetes manifests for deploying a Python web application using blue-green deployment strategy. The manifests are organized in the `manifests` directory and include configurations for deployments, services, Istio resources, and environment variables.

## Directory Structure

```
python-web-manifests
├── manifests
│   ├── deployment-blue.yaml         # Deployment for the blue version of the application
│   ├── deployment-green.yaml        # Deployment for the green version of the application
│   ├── service.yaml                 # Service to route traffic to the application
│   ├── istio-virtualservice.yaml    # Istio VirtualService for traffic routing
│   ├── istio-destinationrule.yaml   # Istio DestinationRule for service subsets
│   ├── istio-gateway.yaml           # Istio Gateway for HTTP traffic
│   ├── env.yaml                     # ConfigMap for environment variables
│   └── kustomization.yaml            # Kustomize configuration for managing resources
├── LICENSE                           # License information for the project
└── README.md                        # Project documentation
```

## Manifests Overview

- **Deployment Manifests**:
  - `deployment-blue.yaml`: Defines a Kubernetes Deployment named "python-web-blue" with 2 replicas.
  - `deployment-green.yaml`: Defines a Kubernetes Deployment named "python-web-green" with 0 replicas.

- **Service Manifest**:
  - `service.yaml`: Defines a Kubernetes Service named "python-web-service" that routes traffic to the application.

- **Istio Manifests**:
  - `istio-virtualservice.yaml`: Defines an Istio VirtualService named "python-web-vs" for traffic routing based on weights.
  - `istio-destinationrule.yaml`: Defines an Istio DestinationRule named "python-web-dr" for service subsets.
  - `istio-gateway.yaml`: Defines an Istio Gateway named "python-web-gateway" that listens for HTTP traffic on port 80.

- **Configuration**:
  - `env.yaml`: Defines a ConfigMap named "env-config" containing environment variables.
  - `kustomization.yaml`: Used by Kustomize to manage the resources and generate the ConfigMap from `env.yaml`.

## Usage

To deploy the application, use the Kubernetes manifests in the `manifests` directory. You can apply the manifests using `kubectl apply -f <manifest-file>`.

## License

This project is licensed under the Apache License 2.0. See the LICENSE file for more details.
# PERN Stack Application on Kubernetes

This repository contains a PERN (PostgreSQL, Express.js, React, Node.js) stack application designed for deployment on a highly scalable Kubernetes cluster. The application is containerized and managed using Helm charts for streamlined deployment and scalability. Additionally, this repository includes a GitHub Actions workflow for automated building and pushing of the application images to Google Cloud Platform's (GCP) Artifact Registry.

## Prerequisites

Before you begin, ensure you have the following installed and configured:

- Docker
- Kubernetes Cluster
- Helm 3
- Google Cloud SDK (gcloud)
- Configured GCP Artifact Registry repository

## Getting Started

1. **Clone the Repository**

    ```bash
    git clone https://github.com/<your-username>/<your-repo-name>.git
    cd <your-repo-name>
    ```

2. **Configure GCP Credentials**

    Ensure that your GCP credentials are configured correctly to allow access to the Artifact Registry. Follow [GCP's documentation](https://cloud.google.com/artifact-registry/docs/docker/authentication) for setting up authentication.

3. **Install Dependencies**

    Navigate to the application directory and install the necessary Node.js dependencies:

    ```bash
    cd app
    npm install
    ```

4. **Local Development**

    Run the application locally for development purposes:

    ```bash
    npm start
    ```

## Deploying with Helm

This repository includes a Helm chart (`pern-chart`) for deploying the application to a Kubernetes cluster.

1. **Navigate to the Helm Chart Directory**

    ```bash
    cd charts/pern-chart
    ```

2. **Install the Helm Chart**

    Customize `values.yaml` as needed for your environment, then install the Helm chart:

    ```bash
    helm install my-pern-app .
    ```

3. **Verify Deployment**

    Check the status of your deployment:

    ```bash
    helm ls
    kubectl get pods
    ```

## Continuous Integration and Delivery (CI/CD)

The `.github/workflows/setup-build-publish.yml` workflow is configured for continuous integration and delivery. This workflow automates the process of building the Docker image for the application, pushing it to the GCP Artifact Registry, and deploying it to the Kubernetes cluster using Helm.

### Workflow Steps:

1. **Build Image**: The application image is built using Docker.
2. **Push Image to GCP Artifact Registry**: The built image is tagged and pushed to the configured GCP Artifact Registry.
3. **Update Helm Chart**: The Helm chart is updated with the new image tag.
4. **Deploy to Kubernetes**: The updated Helm chart is deployed to the Kubernetes cluster.

## Contributing

We welcome contributions! Please read our contributing guidelines before submitting pull requests.

## License

This project is licensed under the [MIT License](LICENSE).

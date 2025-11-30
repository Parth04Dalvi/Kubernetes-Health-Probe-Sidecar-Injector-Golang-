# Kubernetes-Health-Probe-Sidecar-Injector-Golang-
This project is a dedicated command-line utility (CLI) built in Golang that automatically validates and injects standard livenessProbe and readinessProbe configurations into Kubernetes Deployment YAML manifests

Kubernetes Health Probe Sidecar Injector (Golang) 🐳

Overview and Project Goal

This project is a dedicated command-line utility (CLI) built in Golang that automatically validates and injects standard livenessProbe and readinessProbe configurations into Kubernetes Deployment YAML manifests.

This utility directly addresses critical CI/CD and Systems Engineering challenges, ensuring all deployed services meet high-availability standards required by production Kubernetes clusters.

🔑 Key Skills Highlighted

Kubernetes & CI/CD: Demonstrates deep operational understanding of K8s manifest structure and integrating automated validation tools into a CI/CD pipeline (e.g., Jenkins or Gitlab).

Golang for Systems: Uses Go's fast execution speed and standard library (gopkg.in/yaml.v3) for reliable file and configuration parsing.

Configuration Management: Automates the injection of best-practice probe configurations (e.g., initial delay, period, failure thresholds).

Software Engineering: Handles complex YAML structures and serialization/deserialization logic robustly.

⚙️ How the Injector Works

Input: The CLI takes a target Kubernetes YAML file (e.g., deployment.yaml).

Parsing: Go loads and parses the YAML file into structured Go structs, handling the complex nesting of K8s objects (Deployment > Template > Spec > Containers).

Validation/Injection: It iterates through each container:

If livenessProbe is missing, a standard HTTP probe is injected (defaulting to path /healthz on the container port).

If readinessProbe is missing, a standard HTTP probe is injected (defaulting to path /readyz on the container port).

Output: A new file (injected_deployment.yaml) is created with the fully compliant configuration.

Execution

Prerequisites

Go (version 1.18+)

1. Save Files

Save the Go code as main.go and the mock YAML as deployment_mock.yaml.

2. Run the Injector

Execute the Go program from your terminal, passing the mock deployment file as an argument:

go run main.go deployment_mock.yaml


Expected Output

The console will log the processing and the successful creation of a new file named injected_deployment_mock.yaml, which will contain the automatically injected livenessProbe and readinessProbe blocks for the containers.

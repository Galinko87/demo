# README

Using kubectl-ai plugin for generating Kubernetes manifests

## Configuration chart

# README

Description of your project and other essential information.

## YAML Configuration Table

| NAME              | PROMPT                                                                                                                                          | DESCRIPTION                                          | EXAMPLE                                                      |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|--------------------------------------------------------------|
| App Configuration | "create a simple app.yaml with kind Pod app and run: demo, container port: 8000, image - gcr.io/firstcloudproject-419120/demo:v1.0.0"            | Main configuration file for the application.         | [View YAML](./yaml/app.yaml)                                 |
| Liveness Probe    | "create app-livenessProbe yaml metadata: name -app-livenessprob namespace demo; containers: image - same as in app.yaml; port 8000; initial delaysecons - 5; timeout - 1; periodsecond - 10; failure threshold - 3; ports 8080, name http" | YAML for Liveness Probe to check the app's health.   | [View YAML](./yaml/app-livenessProbe.yaml)                   |
| Readiness Probe   | "add readiness probe"                                                                                                                           | YAML for Readiness Probe to check app readiness.     | [View YAML](./yaml/app-readinessProbe.yaml)                  |
| Volume Mounts     | "Create a YAML Pod manifest for Kubernetes with the following specifications: Pod name: app-volume; container based on the image gcr.io/firstcloudproject-419120/demo:v1.0.0; Liveness probe HTTP on /healthy:8080 with delay 5s, period 10s, timeout 1s, max. unsuccessful attempts 3; Readiness probe HTTP on /ready:8080, period 2s, delay 0s, max. 3 unsuccessful, 1 successful; open port 8080 with name http ; data volume \"data\" with hostPath /var/lib/app is mounted in /data" | YAML for configuring volume mounts in containers.    | [View YAML](./yaml/app-volumeMounts.yaml)                    |
| Cron Job          | "create app-cronjob yaml apiVersion batch/v1beta1; kind: CronJob; metadata: name: app-cronjob; schedule: \"*/5 * * * *\" containers: name: hello; image : bash; command: [\"echo\", \"Hello world\"]; restart policy : on failure" | YAML for setting up a Cron Job in Kubernetes.        | [View YAML](./yaml/app-cronjob.yaml)                         |
| Job Configuration | "Create a YAML Job manifest for Kubernetes with the following specifications: Job name: app-job-rsync; mount GCP volume glow-data-disk-200 type ext4 to container named init with image google/cloud-sdk:275.0.0-alpine running gsutil -m rsync -dr gs://glow-sportradar/ /data/input using sh; mount path /data/input; mount name data-input; the container is never reloaded and the backoff limit is 0" | YAML for setting up a Job that runs one-time tasks.  | [View YAML](./yaml/app-job.yaml)                             |
| Multi-container   | "Create a YAML Pod manifest for Kubernetes with the following specifications: Pod name: app-multi-containers; the first container based on the nginx image with the name 1st and by mounting /usr/share/nginx/html; a second container based on the debian image with the name 2nd, the same volume and mount path /html; the second container should add date information to the /html/index.html file every second in an endless loop" | YAML for applications with multiple containers.      | [View YAML](./yaml/app-multicontainer.yaml)                  |
| Resource Limits   | "create K8S manifest for app-resources yaml: Create a YAML pod manifest for Kubernetes with the following specifications: Pod name: app-resource; a container based on the image gcr.io/kuar-demo/kuard-amd64:1 with the name app; Liveness probe HTTP on /healthy:8080 with delay 5s, period 10s, timeout 1s, max. failed attempts 3; Readiness probe HTTP on /ready:8080, period 2s, delay 0s, max. 3 unsuccessful, 1 successful; open port 8080 with name http; and determination of resources and limits of CPU 100m, RAM 256Mi" | YAML for setting resource limits for containers.   | [View YAML](./yaml/app-resources.yaml)                       |
| Secret Environment| "create k8s manifest app-secret-env yaml: Create a YAML Pod manifest for Kubernetes with the following specifications: Pod name: app-secret-env; container based on the redis image with the name mycontainer; two variables SECRET_USERNAME and SECRET_PASSWORD of the secret key mysecret1 are transferred to the environment; the container does not restart" | YAML for configuring secrets in the application environment. | [View YAML](./yaml/app-secret-env.yaml)                  |

## Instructions

Additional instructions or information that may be helpful for users of your repository.

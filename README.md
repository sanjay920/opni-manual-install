# Opni Manual Installation

The best way to install Opni is using `opnictl`.

This repository is to aid in development and should be considered unofficial.

Install Opni manually on an EKS cluster:

| Service name                  | Command                                                                                                                                                                                                                         |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| NATS                          | `helm install nats --set auth.enabled=true,auth.password=VfU6TcAl9x,replicaCount=3,maxPayload=10485760 bitnami/nats`                                                                                                            |
| Traefik                       | `helm install traefik traefik/traefik`                                                                                                                                                                                          |
| Open Distro ES                | `helm install opendistro-es --set elasticsearch.data.persistence.size="100Gi",elasticsearch.client.replicas=3,elasticsearch.data.replicas=3 /Users/sanjay/Desktop/opendistro-build/helm/opendistro-es/opendistro-es-1.13.1.tgz` |
| Minio                         | `helm install --set accessKey=myaccesskey,secretKey=mysecretkey,persistence.size=50Gi minio minio/minio`                                                                                                                        |
| NVIDIA GPU Driver             | `kubectl apply -f https://raw.githubusercontent.com/sanjay920/opni-manual-install/main/nvidia-device-plugin.yaml`                                                                                                               |
| Payload receiver service      | `kubectl apply -f https://raw.githubusercontent.com/sanjay920/opni-manual-install/main/payload-receiver-service.yaml`                                                                                                           |
| Preprocessing service         | `kubectl apply -f https://raw.githubusercontent.com/sanjay920/opni-manual-install/main/preprocessing-service.yaml`                                                                                                              |
| Drain service                 | `kubectl apply -f https://raw.githubusercontent.com/sanjay920/opni-manual-install/main/drain-service.yaml`                                                                                                                      |
| Training controller           | `kubectl apply -f https://raw.githubusercontent.com/sanjay920/opni-manual-install/main/training_controller.yaml`                                                                                                                |
| Nulog inference               | `kubectl apply -f https://raw.githubusercontent.com/sanjay920/opni-manual-install/main/nulog-inference-service.yaml`                                                                                                            |
| Nulog inference control plane | `kubectl apply -f https://raw.githubusercontent.com/sanjay920/opni-manual-install/main/nulog-inference-service-control-plane.yaml`                                                                                              |


____
#### Simulation cluster setup

| Description                    | Command                                                                         |
|--------------------------------|---------------------------------------------------------------------------------|
| Install Sock Shop              | `kubectl apply -f https://raw.githubusercontent.com/sanjay920/opni-manual-install/main/sock-shop-all-in-one.yaml`    |
| Logging config to ship to Opni | `kubectl apply -f https://raw.githubusercontent.com/sanjay920/opni-manual-install/main/setup-logging.yaml`           |
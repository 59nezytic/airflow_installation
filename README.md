# airflow_installation
KubernetesExecutor

```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
source get_helm.sh
```

```
helm repo add stable https://charts.helm.sh/stable
helm search repo stable
helm repo update
```

```
helm repo add airflow-stable https://airflow-helm.github.io/charts
helm repo update
```

(On Worker Node)

```
mkdir -p /data/volumes/postgres
mkdir -p /data/volumes/logs
```


Change postgres, logs YAML FILE {values : NODE_NAME} \n
Change custom_values_v8.5.2 YAML FILE {repo: "https://{GIT ID}:{ACCESS_TOKEN}@github.com/59nezytic/airflow-dag"}

```
k create ns airflow
k apply -f logs.yaml -f postgres.yaml -n airflow
```

```
helm install airflow airflow-stable/airflow --namespace airflow --version "8.5.2" --values ./custom_values_v8.5.2.yaml --debug
```

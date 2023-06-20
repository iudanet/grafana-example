# Стенд Grafana

## Используемые приложения

* grafana/grafana:latest
    * UI Grafana для визуализации метрик и логов
* postgres:15.1
    * База для Grafana. По умолчанию sqlite
* grafana/loki:2.7.1
    * Бекенд для сбора логов
* grafana/promtail:2.7.1
    * Клиентсокое приложение для сбора логов с серверов
* minio/minio
    * Имплементация S3 протокола для хранения файлов. Используется для хранения логов в loki
* prom/prometheus:v2.41.0
    * База данных временных рядов собирающая метрики в своем формате по http, модель pull
* prom/node-exporter:v1.5.0
    * экспортер системных метрик в формат prometheus
* gcr.io/cadvisor/cadvisor:v0.46.0
    * экспортер метрик docker в формат prometheus
* ghcr.io/cablespaghetti/missing-container-metrics:0.22.0
    * экспортер метрик docker в формат prometheus , показывет часть метрики которых нет в cadvisor

## Запуск

```bash
git clone git@github.com:iudanet/grafana-example.git
cd grafana-example

docker compose pull
docker compose up -d

```

## Логи
```bash
docker compose logs -f --tail=1
```

## Статус

```bash
docker compose ps
```

## Urls админок приложений
* [Grafana](http://127.1.1.1:3000)
    * авторизация `admin` : `admin`
* [Promitheus](http://127.1.1.1:9090)
*[Minio](http://127.1.1.1:9001)
    * авторизация `loki` :  `supersecret`


## Доп настройка
 * Импортировать дашборд [Node Exporter](https://grafana.com/graBfana/dashboards/1860-node-exporter-full/)
 * Импортировать дашборд [cAdvisor](https://grafana.com/grafana/dashboards/10657-docker-and-system-monitoring/)

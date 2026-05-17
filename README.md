Во время выполнения задания в WSL2 Filebeat не смог получить доступ к стандартному пути Docker-логов `/var/lib/docker/containers/*/*.log`, так как данный путь был недоступен из текущего окружения.

Для проверки цепочки сбора логов был организован вывод логов контейнера `some_app` в файл `./docker-logs/some_app.log`. Этот файл был примонтирован в контейнер Filebeat по пути `/var/log/docker/some_app.log`.

После этого Filebeat начал читать лог-файл и отправлять события в Logstash. Logstash принял события и записал их в Elasticsearch в индекс `logstash-2026.05.17`.

Итоговая цепочка:

`some_app.log → Filebeat → Logstash → Elasticsearch → Kibana`


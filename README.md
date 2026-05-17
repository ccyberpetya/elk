Во время выполнения задания в WSL2 Filebeat не смог получить доступ к стандартному пути Docker-логов `/var/lib/docker/containers/*/*.log`, так как данный путь был недоступен из текущего окружения.

Для проверки цепочки сбора логов был организован вывод логов контейнера `some_app` в файл `./docker-logs/some_app.log`. Этот файл был примонтирован в контейнер Filebeat по пути `/var/log/docker/some_app.log`.

После этого Filebeat начал читать лог-файл и отправлять события в Logstash. Logstash принял события и записал их в Elasticsearch в индекс `logstash-2026.05.17`.

Итоговая цепочка:

`some_app.log → Filebeat → Logstash → Elasticsearch → Kibana`

# 1
<img width="1278" height="507" alt="1" src="https://github.com/user-attachments/assets/959d3995-d365-423d-9b13-55f945538e97" />
# 2
<img width="1258" height="988" alt="2" src="https://github.com/user-attachments/assets/619723ec-ed82-4c54-80cb-9e4310afc943" />
# 3
<img width="1277" height="1057" alt="3" src="https://github.com/user-attachments/assets/1c720d17-032b-42c0-ac7e-14aed2ba19f2" />
# 4
<img width="953" height="412" alt="4" src="https://github.com/user-attachments/assets/06ca52ac-3b3f-48ca-90a0-acea2b4cfae4" />
# 5
<img width="929" height="95" alt="5" src="https://github.com/user-attachments/assets/c5b4ddea-b7ed-4347-8a0d-d307d73fc163" />
# 6
<img width="1266" height="899" alt="6" src="https://github.com/user-attachments/assets/40bf9d7c-f588-458c-9d85-bf9d6309346d" />

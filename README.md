# Решение тестового задания

1. Для приложения `app,py` был написан Dockerfile

2. Конфиг Prometheus лежит в `prometheus/prometheus.yml`

3. Старт работы
```
docker-compose up
```

Контейнеры запускаются на портах:
* 5000 для flask
* 9090 для prometheus
* 3000 для Grafana

При развертывании конфигурации в prometheus в status/targets можно увидеть Flask

 ![изображение](https://github.com/AsonovNikolay/devops-flask-test/assets/71010958/48c7a3dd-e3be-4cf2-a085-ea0fa4422edb)


4. Далее в Grafana указываем новый datasource. Поскольку контейнеры находятся в одной сети, обращаемся по имени контейнера
(также был указан scrape_interval = 1s)

  ![изображение](https://github.com/AsonovNikolay/devops-flask-test/assets/71010958/338dff4b-3ba6-43aa-a3cd-b0f2c210d34b)




6. В Grafana импортируем новый дашборд при помощи json-конфигурации из
файла `configs/dashboard.json`

  ![изображение](https://github.com/AsonovNikolay/devops-flask-test/assets/71010958/e3382ca9-4890-4f30-8f57-036d7dcd132e)

  Настройки графика выглядят следующим образом:

  ![изображение](https://github.com/AsonovNikolay/devops-flask-test/assets/71010958/1dcadb39-c5a4-40e5-b4d7-e042b335425b)


7. Для стресс тестов был выбран Postman

Конфиг коллекции в файле `configs/devops_test.postman_collection.json`
Для запуска коллекции были выбраны следующие настройки:

  ![изображение](https://github.com/AsonovNikolay/devops-flask-test/assets/71010958/a48b0314-0194-40ba-9de9-cb6f1937a4a0)

8. Результаты тестирования
   
   ![изображение](https://github.com/AsonovNikolay/devops-flask-test/assets/71010958/2e8509c4-05b6-4f1a-93e4-ddfbf7dbb3a6)

   ![изображение](https://github.com/AsonovNikolay/devops-flask-test/assets/71010958/df643c0c-1c77-4dcd-b609-62f7688cd04e)

   При интервале запроса в Postman 10мс Grafana показывает 160 запросов в секунду.

9. Вывод
    
   Приложение справляется с нагрузкой более 100 запросов в секунду.
   При увеличении количества запросов до 200 в секунду среднее время ответа также не меняется.






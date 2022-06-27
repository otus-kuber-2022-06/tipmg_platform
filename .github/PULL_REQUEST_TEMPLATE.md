# Выполнено ДЗ №

 - [ x ] Основное ДЗ
 - [ x ] Задание со *

## В процессе сделано:
 - Пункт 1
    Согласно документации https://kubernetes.io/docs/tasks/administer-cluster/guaranteed-scheduling-critical-addon-pods/
    kube-api pod имеет статус priorityClassName: system-node-critical который гарантирует запуск критически важных pods.
    Поэтому происходит его восстановление после удаление.
    Pod core-dns имеет deployment с replica равное 1. В итоге pod будет восстановлен согласно количеству replica.
    То есть сначала будет восстановлен kube-api, а уже после core-dns.
 - Пункт 2
    Создан docker image tipmg86/web:0.0.1 который работает на 8000 под UID 1001
    и доступен файл homework.html по адресу http://localhost:8000/homework.html
    сам файл находится по пути /app/homework.html
 - Пунк 3
    Создан манифест web-pod.yaml с init container
 - Пунк 4
    Создан манифест frontend-pod-healthy.yaml
## Как запустить проект:
 - docker run -d --name web -p 8000:8000 tipmg86/web:0.0.1
 - kubectl apply -f web-pod.yaml && kubectl port-forward --address 0.0.0.0 pod/web 8000:8000
 - kubectl apply -f frontend-pod-healthy.yaml 
## Как проверить работоспособность:
 - Сервис web, перейти по ссылке http://localhost:8000/homework.html
 - Сервес web с initcontainer, перейти по ссылке http://localhost:8000/index.html
## PR checklist:
 - [ x ] Выставлен label с темой домашнего задания

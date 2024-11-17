## devops_test
Установка и запуск

Предварительные требования

1 Docker

2 Minikube

3 Kubectl

Клонируем репозиторий 

Сам образ приложения на docker.hub 

Его также можно склонировать к себе 
```bash
docker pull she1me/hello:app
```

Запускаем minikube
```bash
minikube start
```
Проверяем доступность нодов 
```bash
kubectl get nodes
```
Применяем конфигурацию манифестов k8s
```bash
kubectl apply -f namespace.yaml
kubectl apply -f deployment.yaml
kubectl appply -f service.yaml
```
Можем посмотреть корректно ли работают наши поды, они должны быть в статусе running и запущено 1/1 контейнер
По умолчанию устанавливается пространство имен default, но для гибкий работы я добавил новый namespace под названием hello-app
```bash
kubectl get pods -n hello-app
```
Чтобы получить доступ к вашему приложению, используйте команду minikube для открытия сервиса
```bash
minikube service hello-service -n hello-app 
```
Если браузер не открывается автоматически, можно использовать следующую команду, чтобы получить URL
```bash
minikube service hello-service -n hello-app --url
```
Вводим url в браузер и получаем работоспособное приложение 

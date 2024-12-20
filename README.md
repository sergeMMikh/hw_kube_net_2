# Домашнее задание к занятию «Сетевое взаимодействие в K8S. Часть 2»- Михалёв Сергей

### Цель задания

В тестовой среде Kubernetes необходимо обеспечить доступ к двум приложениям снаружи кластера по разным путям.

------

### Чеклист готовности к домашнему заданию

1. Установленное k8s-решение (например, MicroK8S).
2. Установленный локальный kubectl.
3. Редактор YAML-файлов с подключённым Git-репозиторием.

------

### Инструменты и дополнительные материалы, которые пригодятся для выполнения задания

1. [Инструкция](https://microk8s.io/docs/getting-started) по установке MicroK8S.
2. [Описание](https://kubernetes.io/docs/concepts/services-networking/service/) Service.
3. [Описание](https://kubernetes.io/docs/concepts/services-networking/ingress/) Ingress.
4. [Описание](https://github.com/wbitt/Network-MultiTool) Multitool.

------

### Задание 1. Создать Deployment приложений backend и frontend

1. Создать Deployment приложения _frontend_ из образа nginx с количеством реплик 3 шт.
2. Создать Deployment приложения _backend_ из образа multitool. 
3. Добавить Service, которые обеспечат доступ к обоим приложениям внутри кластера. 
4. Продемонстрировать, что приложения видят друг друга с помощью Service.
5. Предоставить манифесты Deployment и Service в решении, а также скриншоты или вывод команды п.4.

**Решение**

1. Для пешения задачи создал манифесты:

для frontend:
- [frontend-deployment.yaml](manifests/frontend-deployment.yaml)
- [frontend-service.yaml](manifests/frontend-service.yaml)

для backend:
- [backend-deployment.yaml](manifests/backend-deployment.yaml)
- [backend-service.yaml](manifests/backend-service.yaml)

2. Запустил сервисы:</br>
<img src="images/Task_1_1.png" alt="Task_1_1.png" width="400" height="auto"></br>

3. Проверка доступности сервиса frontend для backend:</br>
<img src="images/Task_1_2.png" alt="Task_1_2.png" width="400" height="auto"></br>
Проверка доступности сервиса backend для frontend:</br>
<img src="images/Task_1_3.png" alt="Task_1_3.png" width="400" height="auto"></br>
------

### Задание 2. Создать Ingress и обеспечить доступ к приложениям снаружи кластера

1. Включить Ingress-controller в MicroK8S.
2. Создать Ingress, обеспечивающий доступ снаружи по IP-адресу кластера MicroK8S так, чтобы при запросе только по адресу открывался _frontend_ а при добавлении /api - _backend_.
3. Продемонстрировать доступ с помощью браузера или `curl` с локального компьютера.
4. Предоставить манифесты и скриншоты или вывод команды п.2.

**Решение**
1. Включил Ingress-controller в MicroK8S.</br>
<img src="images/Task_2_1.png" alt="Task_2_1.png" width="400" height="auto"></br>
2. Манифест [ingress.yaml](manifests/ingress.yaml)
3. Проверяем работу </br>
<img src="images/Task_2_2.png" alt="Task_2_2.png" width="400" height="auto"></br>
4. Доступность frontend: </br>
<img src="images/Task_2_3.png" alt="Task_2_3.png" width="400" height="auto"></br>
5. Доступность api:</br>
<img src="images/Task_2_4.png" alt="Task_2_4.png" width="400" height="auto"></br>
6. Доступность frontend извне по IP виртуальной машины:</br>
<img src="images/Task_2_5.png" alt="Task_2_5.png" width="400" height="auto"></br>
7. Доступность api извне по IP виртуальной машины:</br>
<img src="images/Task_2_6.png" alt="Task_2_6.png" width="400" height="auto"></br>

------



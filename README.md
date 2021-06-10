# wargaming-test
Тестовое задание для соискателя на вакансию DevOps Engineer

## Подготовка
Для выполнения тебе понадобится зарегистрировать бесплатный AWS аккаунт. Насчет средств
можешь не беспокоиться - мы обойдемся включенными во free tier ресурсами:
https://aws.amazon.com/ru/free/

Также для выполнения понадобится:
- пара ssh-ключей (их нужно создать вручную в web-консоли AWS и назвать, например, wgmoscow-test)
- S3-бакет (его тоже нужно создать вручную)

## Задание №1
Описать в Terraform создание таких сущностей в AWS:
- 1 VPC
- 1 subnet в этом VPC
- 1 internet gateway
- таблица маршрутизации для создаваемого VPC должна содержать правило,
позволяющее любому трафику проходить через internet gateway
- 1 security group, разрешающая доступ с любых ip-адресов по порту 22
- 1 security group, разрешающая доступ с любых ip-адресов по порту 80 и 443
- 1 ЕС2-инстанс с установленной Ubuntu 20.04 LTS, к которому можно подключиться по
ssh используя ключ, которые был создан ранее вручную
Регион можно выбрать любой. Все создаваемые Terraform сущности должны быть
протегированы (тег можно назначить любой). Также нужно настроить сохранение состояния
Terraform в ранее созданный S3-бакет. Если не получается описать какую-то сущность кодом в
Terraform - можно создать эту сущность вручную.

## Задание №2
При помощи Ansible описать для ЕС2-инстанса, созданного в задании №1, такие действия:
- обновление репозиториев
- создание пустого файла empty.txt с правами 600 в каталоге /data
- деплоймент веб-сервера nginx
- на приветственной странице nginx должно быть написано “Hello from
<локальный_ip_адрес_инстанса>”
Nginx должен подниматься и работать даже после перезагрузки ЕС2-инстанса.

## Проверка
Задание считается полностью выполненным, если в облаке AWS создан VPC, subnet, internet
gateway, 2 security group’ы, ЕС2-инстанс. На инстансе установлен nginx, который работает на 80
порту и отвечает на запросы извне, показывая кастомное приветствие. Также на инстанс можно
зайти по ssh.
Отправка результатов
Результат задания опубликуй в свой личный репозиторий в GitHub и приложи ссылку, чтобы мы
могли его посмотреть. Отправь ответ даже если ты выполнил не все задания. Просто опиши с
какими трудностями ты столкнулся и как пробовал их решить.
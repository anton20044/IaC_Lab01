Лабораторная работа №1 по курсу IaC.

Задание:

Установите Yandex.CLI: https://cloud.yandex.ru/docs/cli/operations/install-cli
Установите Packer: https://www.packer.io/ https://cloud.yandex.ru/docs/tutorials/infrastructure-management/packer-quickstart
Подключитесь при помощи Yandex.CLI к облаку и просмотрите конфигурацию:
yc init
yc config list
Склонируйте к себе репозиторий https://github.com/timurb/otus-packer и создайте у себя в облаке образ:
packer build json/template.json
(понадобится установить переменные)
5 (). Создайте сервисную учетную запись для packer:
yc iam service-account create --name packer --folder-id XXXXXXXXXXXXX
yc iam service-account get
yc resource-manager folder add-access-binding --id XXXXXXXXXXXXX --role editor --service-account-id XXXXXXXXXXXXXXX
yc iam key create --service-account-id XXXXXXXXXXXXXXX --output key.json
6 (). Вставьте путь к вашему ключу в template.json в "service_account_key_file" в блок builders и создайте из этого шаблона образ
(вероятно понадобится удалить из шаблона параметр token)
7 (*). Параметризуйте сборку, например добавьте установку image_description пользователем
Удалите созданные образы:
yc compute image list
yc compute image delete
Пришлите последние строчки вывода packer build (те, в которых указан id) и получившийся в финале template.json

Решение:

Задание выполнено по шагам, вывод сборки Packer прилагаю на скриншоте 1.
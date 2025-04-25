# Домашнее задание к занятию 17.2 «Работа с Playbook» - Падеев Василий


## Подготовка к выполнению

1. * Необязательно. Изучите, что такое [ClickHouse](https://www.youtube.com/watch?v=fjTNS2zkeBs) и [Vector](https://www.youtube.com/watch?v=CgEhyffisLY).  
2. Создайте свой публичный репозиторий на GitHub с произвольным именем или используйте старый.  
3. Скачайте [Playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.  
4. Подготовьте хосты в соответствии с группами из предподготовленного playbook.  

## Основная часть

1. Подготовьте свой inventory-файл `prod.yml`.  

С помощью Terraform запустил ВМ Centos7 в Yandex Cloud. Подгоговил [prod.yml](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/playbook/inventory/prod.yml)   

2. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает [vector](https://vector.dev). Конфигурация vector должна деплоиться через template файл jinja2. От вас не требуется использовать все возможности шаблонизатора, просто вставьте стандартный конфиг в template файл. Информация по шаблонам по [ссылке](https://www.dmosk.ru/instruktions.php?object=ansible-nginx-install). не забудьте сделать handler на перезапуск vector в случае изменения конфигурации!  

Обновленная конфигурация [playbook](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/playbook/site.yml)  

3. При создании tasks рекомендую использовать модули: `get_url`, `template`, `unarchive`, `file`.  
4. Tasks должны: скачать дистрибутив нужной версии, выполнить распаковку в выбранную директорию, установить vector.  
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.  

Найдены ошибки отсутствие имени block и новой строки в конце файла.  

![answer1](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/png/2.png)  
![answer1](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/png/3.2.png)  
Полностью исправить все ошибки на хостовой машине с ОС Ubuntu не представляется возможным. Проверку продолжил на ВМ Centos7  

![answer1](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/png/3.png)  

6. Попробуйте запустить playbook на этом окружении с флагом `--check`.  

Ошибка связана с неверной ссылкой.
![answer1](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/png/4.png)  

7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены.  

![answer1](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/png/4.png)  
![answer1](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/png/5.png)  

8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен.  

![answer1](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/png/6.png)  
![answer1](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/png/7.png)  
![answer1](https://github.com/Vasiliy-Ser/working_with_playbook_17.2/blob/61140f9685f084bcdaa34c3ec3995fbbe7df72bf/png/8.png)  

9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги. Пример качественной документации ansible playbook по [ссылке](https://github.com/opensearch-project/ansible-playbook). Так же приложите скриншоты выполнения заданий №5-8  
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-02-playbook` на фиксирующий коммит, в ответ предоставьте ссылку на него.  


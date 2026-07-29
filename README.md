# Found-MySQL-service-with-empty-root-password-BITRIX-VA

При попытке создать допополнительный сайт menu.sh показывает «Found MySQL service with empty root password», но пароль задан и все работает.

Смена пароля через menu.sh не помогает.

Метод обхода ошибки с помощью подмены закешированного результата проверки:

1. Логинимся в первой консоли как root и запускаем menu.sh

2. Создаем сайт и доходим до момента, когда появляется сообщение «Found MySQL service with empty root password»

3. Параллельно открываем вторую консоль (второй сеанс) и открываем файл /opt/webdir/tmp/mysql_servers_status.cache — в нем должен быть список значений, разделенных «:»

4. На 3-м и 2-м месте с конца находятся параметры, отвечающие за сообщения  «Found MySQL service with empty root password» и «Not found MySQL client config». Заменяем «N:N» на «Y:Y»

5. Сохраняем файл не закрывая консоль

6. Возвращаемся в первую консоль и пытаемся добавить сайт еще раз.

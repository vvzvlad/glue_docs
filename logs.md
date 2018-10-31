# Система логов

## Зачем нужна система логгирования

Важная часть разработки — отладка и логгирование. Glue предоставляет расширенную систему логгирования, которая одновременно позволяет просматривать логи каждого скрипта и драйвера во время разработки, и показывать логи всех скриптов в едином месте.  
Каждая запись в логе обладает уровнем: **ERROR**, **WARNING**, **INFO** и **USER**. Сортировка по уровням позволяет сократить время на просмотр логов, ограничившись только важными записями, например, с уровнем **ERROR**.  

Создать запись в логе очень просто: можно использовать функции `log_error`, `log_warning`, `log_user`, передавая им в качестве одного или нескольких аргументов строки, числа или таблицы, которые вы хотите записать в лог:  
`log_user("Log entry", 2, {data=12})`  

Также можно использовать функции `log()` или `print()` — эти функции являются алиасами к `log_user()`, и создают запись в логе с уровнем **USER**.   
Подробнее о использовании функций, смотрите раздел "Документация разработчика" — "Функции для работы с логами".   

## Уровни логгирования

Идеология системы требует, чтобы записи с уровнем **ERROR** возникали в случаях, когда нормальная работы системы нарушена, и необходимо внешнее вмешательство для исправления проблем.  
Записи с уровнем **WARNING** — в ситуациях, когда возникла ошибка, но система может продолжать работу, несмотря на то, что ошибка требует исправления.  
Записи с уровнем **INFO** — тогда, когда вмешательство не требуется в данный момент, но все же информацию надо передеать оператору.  
Записи с уровнем **USER** служат для отладки или информационных сообщений в процессе работы. Предполагается, что при обслуживании они могут быть проигнорированы, если только не сопровождаются записью другого уровня, а сами служат лишь дополнительной информацией для восстановления картины происходящего.  

Вышеприведенные правила — не обязательные, но следование им позволяет создавать поддерживаемые системы.  
## Context

Была применена микросервисная архитектура. Приложение состоит из нескольких сервисов и их экземпляров запущенных на множестве машин. Запросы часто затрагивают(span) несколько сервисов. Каждый сервис пишет логи в стандартизированном формате в log-file.

Как отслеживать поведение приложения и устранять ошибки? Решение должно иметь минимум влияния на runtime.

## Solution

Использовать централизованный сервис логирования, такой как ELK (Kibana в нашем фокусе). Пользователи могут искать и отслеживать логи. Также можно указать уведомления при появлении определенных сообщений в логах.

## Resulting context

* Поддержка такого большого объема данных требует хорошей инфраструктуры.
	* Скорее имеется ввиду, что условный Elastic Search будет жирным с его индексами и количеством логов.

## Related
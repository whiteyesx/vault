
## Context

*  Сервису необходимо предоставить конфигурацию для подключения к внешним сервисам. Например расположение базы данных и credentials.
* Сервис должен запускаться в разных окружениях - dev, text, qa без модификаций кода и рекомпиляции.
* Разные окружения используют разные экземпляры внешних сервисов, например QA database | Production database.

## Solution

Вынести конфигурацию приложения во внешнее окружение (ориг. externalize). При старте приложение считывает конфигурацию с внешнего источника, например переменные окружения OS, Vault, etc.


## Resulting context

### Benefits

*  Приложения запускается с разной конфигурацией без модификаций кода и перекомпиляции.

### Drawbacks

* Как убедиться в том, что приложение было запущенно с конкретной конфигурацией.
	* P.S. Подтянуты они или нет и так нельзя было узнать, можно просто смотреть в ```ConfigMap```

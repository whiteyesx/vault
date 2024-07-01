## Context

Был применен шаблон ```Database per Service``` . Некоторые транзакции охватывают сразу несколько микросервисов, вам нужно реализовать механизм транзакции затрагивающие это сервисы. 

Допустим у нас есть интернет магазин. Приложение должно удостовериться, что новый заказ не превысит пользовательский кредитный лимит. Так как Order и Customer  это два разных сервиса, то мы не можем использовать локальную ACID транзакцию.

* 2PC не является доступным

## Solution

Реализовать каждую бизнес транзакцию охватывающую несколько сервисов как **Saga**. Saga - последовательность локальных транзакций. Каждая локальная транзакция обновляет базу данных и публикует сообщение для триггера следующей локальной транзакциии в Saga. Если одна из транзакций падает с ошибкой, saga выполняет ряд компенсирующих транзакций, чтобы отменить изменения предыдущих локальных транзакций.

Существует для типа реализации Saga:
* Оркестрация - выделяется централизированный сервис, который управляет внешней транзакцией.
* Хореография - каждый сервис знает о последовательности выполнения внешней транзакции.

## Resulting Context
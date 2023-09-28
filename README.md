# Microservice architecture  


### Масштабирование:

<details>
    <summary>Способы масштабирования веб-приложений</summary> 
    <image
    src="/images/1.png">
</details>  
  

<details>
    <summary>Масштабирование по оси Х (горизонтальное)</summary> 
    <image
    src="/images/2.png">
</details>  
  
<details>
    <summary>Масштабирование по оси Z (запросы в зависимости от атрибутов)</summary> 
    <image
    src="/images/3.png">
</details>  

<details>
    <summary>Масштабирование по оси Y (разбивка на разные сервисы, с разными функциями)</summary> 
    <image
    src="/images/4.png">
</details> 

### Архитектура, сравнение, связанность:
<details>
    <summary>Сравнение микросервисов и SOA</summary> 
    <image
    src="/images/5.png">
</details>

<details>
    <summary>Пример слабой связанности и развертываемости микросервисов</summary> 
    <image
    src="/images/6.png">
</details>

<details>
    <summary>Пример шестигранной(гексогональной) архитектуры</summary> 
    <image
    src="/images/7.png">
</details>  

<details>
    <summary>Подробный пример микросервисной архитектуры</summary> 
    <image
    src="/images/8.png">
</details>  

<details>
    <summary>Типы запросов в микросервисах: команды и запросы</summary> 
    <image
    src="/images/9.png">
</details>  

## Межпроцессное взаимодействие в микросервисной архитектуре  
### Типы взаимодействия:
* **REST** предоставляет набор архитектурных ограничений, которые, если их применять как единое целое, делают
акцент на масштабируемости взаимодействия между компонентами, обобщенности интерфейсов, независимом развертывании компонентов и промежуточных компонен­тах, чтобы снизить латентность взаимодействия, обеспечить безопасность и ин­капсулировать устаревшие системы  

* **gRPC** - это фреймворк для написания многоязыч­ных клиентов и серверов (см. ru.Wikipedia.org/wiki/Удалённый-ВызоВ-Процедур). gRPC представляет собой двоичный протокол на основе сообщений. Как вы помните из обсуждения двоичных форматов, это означает, что проектирование сервиса должно начинаться с его API. API в gRPC описывается с помощью языка IDL на основе Protocol Buffers — многоязычного механизма сериализации структурированных данных от компании Google.  
*  **Взаимодействие с помощью асинхронного обмена сообщениями (брокеры сообщений):**
<ul>
<details>
    <summary>Реализация синхронных и асинхронных запросов/ответов</summary> 
    <image
    src="/images/13.png">
</details>  
<details>
    <summary>Сравнение взаимодействия на прямую и через брокер сообщений</summary> 
    <image
    src="/images/14.png">
</details>  
</ul>

### Восстановление и обнаружение:
<details>
    <summary>Восстановление после отказа сервиса</summary> 
    <image
    src="/images/10.png">
</details>  

<details>
    <summary>Обнаружение сервисов на уровне приложения</summary> 
    Смысл: Сетевое местоположение назначается экземплярам сервисов динамически. Более
того, набор этих экземпляров постоянно меняется из-за автоматического масшта­
бирования, отказов и обновлений. Из-за этого ваш клиент должен использовать
обнаружение сервисов.
    <image
    src="/images/11.png">
</details>  

<details>
    <summary>Применение шаблонов обнаружения сервисов,
предоставляемых платформой</summary> 
    <image
    src="/images/12.png">
</details>  

### Управление транзакциями в микросервисной архитектуре  


<details>
    <summary>Операция createOrder() обновляет данные в нескольких сервисах</summary> 
    <image
    src="/images/15.png">
</details>  

<details>
    <summary>Пример повествования: создание заказа</summary> 
    <image
    src="/images/16.png">
</details>  

<details>
    <summary>Повествования, основанные на хореографии</summary> 
    Хореография — это один из способов реализации повествований. Она не предусма­
тривает центрального координатора, который выдает участникам команды. Вместо
этого участники подписываются на события друг друга и реагируют соответству­
ющим образом.
    <image
    src="/images/17.png">
</details>  

<details>
    <summary>Повествования на основе оркестрации</summary> 
    Оркестрация — это еще один способ реализации повествований. Она подразумевает
определение класса-оркестратора, единственной задачей которого является рассыл­
ка инструкций участникам. Оркестратор взаимодействует с участниками в стиле
«команда/асинхронный ответ».
    <image
    src="/images/18.png">
</details>  

<details>
    <summary>Моделирование оркестраторов повествований
в виде конечных автоматов</summary> 
Конечный автомат — это хорошая модель для оркестратора повествования. Он со­
стоит из набора состояний и переходов между ними, которые инициируются с по­
мощью событий. У каждого перехода может быть какое-то действие, которое в кон­
тексте повествования означает вызов участника.
    <image
    src="/images/19.png">
</details>  

<details>
    <summary>Пример архитектуры сервиса Order и его повествований</summary> 
    <image
    src="/images/20.png">
</details>  

<details>
    <summary>Фреймворк Eventuate Tram Saga для создания повествований</summary> 
    <image
    src="/images/21.png">
</details>  

### Шаблоны организации бизнес-логики  

<details>
    <summary>Проектирование бизнес-логики с помощью
шаблона «Сценарий транзакции»</summary> 
    <image
    src="/images/22.png">
</details>  

<details>
    <summary>Проектирование бизнес-логики с помощью
шаблона «Доменная модель»</summary> 
    <image
    src="/images/23.png">
</details>  

<details>
    <summary>Шаблон "Агрегат"</summary> 
    Агрегат — это кластер доменных объектов, с которыми можно обращаться как с еди­
ным целым. Он состоит из корневой сущности и иногда одной или нескольких сущ­
ностей и объектов значений.
    <image
    src="/images/24.png">
</details>  

<details>
    <summary>Правила для агрегатов</summary> 
    <ul>
    <li>
    Правило 1. Ссылайтесь только на корень агрегата  
    Оно требует,
чтобы корневая сущность была единственной частью агрегата, на которую могут
ссылаться внешние классы. Для обновления агрегата клиенту необходимо вызвать
метод из его корня.
    </li>
    <li>
    Правило 2. Межагрегатные ссылки
должны применять первичные ключи  
I [равило состоит в том, что агрегаты ссылаются друг на друга по уникальному зна­
чению, например по первичному ключу, а не по объектным ссылкам.
<image
    src="/images/25.png">
    </li>
    <li>
    Правило 3. Одна транзакция создает или обновляет один агрегат  
    транзакция может создать или обновить только один агрегат
    </li>
    </ul>
    <image
    src="/images/26.png">
</details>

<details>
    <summary>Проектирование бизнес-логики
с помощью агрегатов</summary> 
    <image
    src="/images/27.png">
</details>  

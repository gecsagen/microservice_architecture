# Микросервисная архитектура  
*Основано на книге: Микросервисы. "Паттерны разработки и рефакторинга" - Ричардсон Крис.* 

## Часть 1
<details>
<summary>Масштабирование</summary> 
<ul>
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
</ul>
</details>

## Часть 2
<details>
<summary>Архитектура, сравнение, связанность:</summary> 
<ul>
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
</ul>
</details>

## Часть 3
<details>
<summary>Межпроцессное взаимодействие и их типы</summary> 
<ul>
<details>
    <summary>REST</summary> 
    <p>Предоставляет набор архитектурных ограничений, которые, если их применять как единое целое, делают акцент на масштабируемости взаимодействия между компонентами, обобщенности интерфейсов, независимом развертывании компонентов и промежуточных компонен­тах, чтобы снизить латентность взаимодействия, обеспечить безопасность и ин­капсулировать устаревшие системы  </p>
</details>  

<details>
    <summary>gRPC</summary> 
    <p>Это фреймворк для написания многоязыч­ных клиентов и серверов (см. ru.Wikipedia.org/wiki/Удалённый-ВызоВ-Процедур). gRPC представляет собой двоичный протокол на основе сообщений. Как вы помните из обсуждения двоичных форматов, это означает, что проектирование сервиса должно начинаться с его API. API в gRPC описывается с помощью языка IDL на основе Protocol Buffers — многоязычного механизма сериализации структурированных данных от компании Google.  </p>
</details>  
<details>
<summary>Взаимодействие с помощью асинхронного обмена сообщениями (брокеры сообщений)</summary>
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
</details>
</ul>
</details>

## Часть 4
<details>
<summary>Восстановление и обнаружение</summary> 
<ul>
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
</ul>
</details>  

## Часть 5 
<details>
<summary>Управление транзакциями в микросервисной архитектуре</summary> 
<ul>

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
</ul>
</details>

## Часть 6  
<details>
<summary>Шаблоны организации бизнес-логики </summary> 
<ul>
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

<details>
    <summary>Бизнес-логика сервиса Kitchen (пример)</summary> 
    <image
    src="/images/28.png">
</details>  

<details>
    <summary>Бизнес-логика сервиса Order (пример)</summary> 
    <image
    src="/images/29.png">
</details>  
</ul>
</details> 

##  Часть 7 
<details>
<summary>Разработка бизнес-логики с порождением событий</summary> 
<ul>
<details>
    <summary>Шаблон "Порождение событий"</summary> 
    Сохраняет агрегат в виде последовательности доменных событий, которые представляют
    изменения состояния: см <a href="https://microservices.io/patterns/data/event-sourcing">https://microservices.io/patterns/data/event-sourcing</a>
    <image
    src="/images/30.png">
</details>  


<details>
    <summary>Развитие доменных событий</summary> 
    <p>Существует вероятность того, что приложению придется иметь дело с несколь­
кими версиями событий. Например, у сервиса, загружающего агрегат Order, может
возникнуть необходимость в сохранении разных версий событий.</p>
    <image
    src="/images/31.png">
</details>  

<details>
    <summary>Реализация хранилища событий</summary> 
    <p>Хранилище событий — это гибрид базы данных и брокера сообщений.
Оно ведет себя как БД, потому что у него есть API для вставки и извлечения событий
агрегата по первичному ключу. Но оно похоже и на брокер сообщений, потому что
у него есть API, который позволяет подписываться на события.</p>
    <image
    src="/images/32.png">
</details>  
</ul>
</details>  

##  Часть 8  
<details>
<summary>Реализация запросов в микросервисной архитектуре</summary> 
<ul>
<details>
    <summary>Выполнение запросов с помощью объединения API</summary> 
    <p>Операция findOrder() извлекает заказ по его первичному ключу. Она принимает
orderld в качестве параметра и возвращает объект OrderDetails, который содержит
информацию о заказе</p>
    <image
    src="/images/33.png">
</details>  

<details>
    <summary>Обзор шаблона «Объединение API»</summary> 
    <image
    src="/images/34.png">
</details>  

<details>
    <summary>Пример реализации объеденения API</summary> 
    <image
    src="/images/35.png">
</details>  

<details>
    <summary>Обзор CQRS</summary> 
    <p>
    CQRS расшифровывается как разделение ответственности командных запросов.
Как следует из названия, этот шаблон предназначен для разделения обязанностей.
    </p>
    <image
    src="/images/36.png">
</details>  

<details>
    <summary>QRS и сервисы, предназначенные только для запросов</summary> 
    <image
    src="/images/37.png">
</details>  
</ul>
</details>
# Домашнее задание к занятию «Микросервисы: принципы»

## Задача 1: API Gateway
Предложите решение для обеспечения реализации API Gateway. Составьте сравнительную таблицу возможностей различных программных решений. На основе таблицы сделайте выбор решения.

Решение должно соответствовать следующим требованиям:

маршрутизация запросов к нужному сервису на основе конфигурации,
возможность проверки аутентификационной информации в запросах,
обеспечение терминации HTTPS.
Обоснуйте свой выбор.

| Решение	| Маршрутизация запросов	| Проверка при аутентификации |	Аутентификация | Терминация HTTPS | Open source | Поддерживаемые типы API|
|---|---|---|---|---|---|---|
|Gloo Gateway|Очень гибкая (L7, header, path, function-level)|Да|JWT, OIDC, API keys, mTLS, LDAP, внешние сервисы (из коробки в Enterprise)|Да|Частично|REST, gRPC, GraphQL, WebSocket, TCP|
|Envoy Gateway|Очень гибкая (virtual hosts, weighted, SNI)|Да|JWT-фильтр, ExtAuthN/ExtAuthZ, mTLS (через фильтры/плагины)|Да|Полностью|REST, gRPC, HTTP/2, WebSocket, TCP/UDP|
|Kong Gateway|Path/host/header, service-based|Да|JWT, OAuth2, OIDC, ACL, LDAP, mTLS (через плагины)|Да|Да|REST, gRPC, GraphQL, WebSocket|
|NGINX/NGINX Plus|Path/host/regex, L7/TCP|Да|OSS: базовые механизмы (basic auth, lua); Plus: JWT, OIDC|Да|Да, кроме Plus|REST, gRPC, HTTP/2, WebSocket, TCP|
|Traefik|Path/host, labels, CRD|Да|JWT, Basic, Forward Auth, OIDC (через middleware)|Да|Да|REST, gRPC, HTTP/2, TCP/UDP, WebSocket|
|AWS API Gateway|Path, stage, route|Да|IAM, Cognito, JWT/OIDC, Lambda authorizers, mTLS|Да|Нет|REST, HTTP, WebSocket (gRPC/GraphQL через Lambda/proxy)|
|Tyk Gateway|Path/host/header|Да|JWT, OAuth2, OIDC, HMAC, mTLS|Да|Да|REST, GraphQL, gRPC, Async APIs|



## Задача 2: Брокер сообщений
Составьте таблицу возможностей различных брокеров сообщений. На основе таблицы сделайте обоснованный выбор решения.

Решение должно соответствовать следующим требованиям:

поддержка кластеризации для обеспечения надёжности,
хранение сообщений на диске в процессе доставки,
высокая скорость работы,
поддержка различных форматов сообщений,
разделение прав доступа к различным потокам сообщений,
простота эксплуатации.
Обоснуйте свой выбор.

# IoT Backend Platform 

## Описание

Это простой **бэкенд-проект** на **Spring Boot + PostgreSQL**.
Проект создан для управления IoT-устройствами: хранение данных, добавление, обновление и удаление.

---

## Как запустить

### 1. Настроить базу данных PostgreSQL

```sql
CREATE USER iot_user WITH PASSWORD 'iot_pass';
CREATE DATABASE iot_platform OWNER iot_user;
```

### 2. Указать настройки в `application.properties`

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/iot_platform
spring.datasource.username=iot_user
spring.datasource.password=iot_pass
spring.jpa.hibernate.ddl-auto=update
```

### 3. Запустить проект

```bash
mvn spring-boot:run
```

---

##  API эндпоинты

* `GET /api/devices` → список всех устройств
* `GET /api/devices/{id}` → устройство по ID
* `POST /api/devices` → добавить устройство
* `PUT /api/devices/{id}` → обновить устройство
* `DELETE /api/devices/{id}` → удалить устройство

---

## Примеры запросов (Postman)

### Добавить устройство (POST)

```json
{
  "name": "HumiditySensor",
  "model": "HS-300",
  "manufactureYear": 2025,
  "description": "Датчик влажности",
  "price": 35.5
}
```

### Получить список (GET)

```
http://localhost:8080/api/devices
```

---

## Что сделано

* Модель данных: `Device` (название, модель, год выпуска, описание, цена, дата добавления)
* CRUD API для устройств
* Данные сохраняются в PostgreSQL

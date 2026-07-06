## /pay-in/create-chargeback

Метод для создания запроса на возврат средств (чарджбэк) по успешной транзакции.
#### url: https://lk.payin-payout.net/pay-in/create-chargeback

### Параметры запроса

| Параметр | Тип | Обязательный | Описание |
| :--- | :--- | :---: | :--- |
| `id_order` | string | Да | ID транзакции в шлюзе. Можно найти в отчетах в личном кабинете. |
| `api_key` | string | Да | Ключ API. Берется в личном кабинете в разделе `/app/#/application`. |
| `partial_chargeback` | string | Нет | Флаг активации частичного возврата. Для включения передайте `"true"`. |
| `partial_chargeback_amount` | float | Нет | Сумма частичного возврата. Обязателен, если `partial_chargeback` передан как `"true"`. |

### Примеры запросов

#### Полный возврат (чарджбэк)

**Запрос:**

```json
{
  "id_order": "{{paymentId}}",
  "api_key": "{{ApiKey}}"
}
```

**Ответ:**
```json
{
    "status": true,
    "message": "Запрос на чарджбэк отправлен на шлюз. Скоро будет произведён чарджбэк!"
}
```
#### Частичный возврат (partial chargeback)
**Запрос:**

```json
{
  "id_order": "{{paymentId}}",
  "api_key": "{{ApiKey}}",
  "partial_chargeback": "true",
  "partial_chargeback_amount": 2500.50
}
```
**Ответ:**

```json
{
    "status": true,
    "message": "Запрос на чарджбэк отправлен на шлюз. Скоро будет произведён чарджбэк!"
}
```

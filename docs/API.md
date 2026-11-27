# API Документация

## Авторизация
Все запросы к API требуют передачи токена в заголовке:
`Authorization: Bearer <ваш_токен>`

---

## 1. Получить список задач
**Метод и путь:** `GET /api/tasks`

**Параметры запроса (Query):**
* `status` (необязательный) — фильтр по статусу (`open`, `done`).

**Пример запроса (cURL):**
```bash
curl -X GET "https://example.com" -H "Authorization: Bearer token123"
```

**Пример ответа (200 OK):**
```json
[
  {
    "id": 1,
    "title": "Изучить Git и GitHub",
    "status": "open"
  }
]
```

**Коды ответа:**

| Код | Описание |
| :--- | :--- |
| **200** | Успешное получение списка |
| **401** | Неверный или отсутствует токен авторизации |

---

## 2. Создать новую задачу
**Метод и путь:** `POST /api/tasks`

**Тело запроса (JSON):**
```json
{
  "title": "Настроить GitHub Pages"
}
```

**Пример запроса (cURL):**
```bash
curl -X POST "https://example.com" \
  -H "Authorization: Bearer token123" \
  -H "Content-Type: application/json" \
  -d '{"title": "Настроить GitHub Pages"}'
```

**Пример ответа (201 Created):**
```json
{
  "id": 2,
  "title": "Настроить GitHub Pages",
  "status": "open"
}
```

**Коды ответа:**

| Код | Описание |
| :--- | :--- |
| **201** | Задача успешно создана |
| **400** | Ошибка валидации (пустое поле `title`) |
| **401** | Ошибка авторизации |

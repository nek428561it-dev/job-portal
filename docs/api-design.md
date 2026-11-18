# REST API проєкту JobPortal

Базова адреса: `http://localhost:3000/api`

| # | Ресурс | Метод | Призначення | Успіх | Помилки |
|---|---|---|---|---|---|
| 1 | `/companies` | GET | перелік компаній | 200 | 500 |
| 2 | `/companies/:id` | GET | одна компанія | 200 | 404 |
| 3 | `/companies/:id/vacancies` | GET | вакансії компанії | 200 | 404 |
| 4 | `/vacancies` | GET | перелік вакансій із фільтрацією | 200 | 400 |
| 5 | `/vacancies/:id` | GET | картка вакансії | 200 | 404 |
| 6 | `/vacancies` | POST | створення вакансії | 201 | 422 |
| 7 | `/vacancies/:id` | PUT | повне оновлення вакансії | 200 | 404, 422 |
| 8 | `/vacancies/:id` | DELETE | видалення вакансії | 204 | 404 |
| 9 | `/applications` | POST | подання відгуку (резюме) | 201 | 422 |

## Параметри GET /vacancies
| Параметр | Тип | Приклад | Опис |
|---|---|---|---|
| `location` | string | `?location=Київ` | фільтр за містом |
| `minSalary` | int | `?minSalary=30000` | нижня межа зарплати |
| `q` | string | `?q=developer` | пошук за назвою або описом |
| `sort` | enum | `?sort=salary_desc` | сортування (за зарплатою чи датою) |
| `page` | int | `?page=2` | номер сторінки |

## Формат помилки
```json
{
  "error": "VALIDATION_FAILED",
  "details": {
    "email": "Має бути коректною e-mail адресою"
  }
}
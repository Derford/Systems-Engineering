# OpenAPI / Swagger

Ниже приведён учебный вариант API. Его можно вставить в Swagger Editor.

```yaml
openapi: 3.0.3
info:
  title: University Career Marketplace API
  version: 1.0.0
  description: API маркетплейса вакансий и стажировок для университета
servers:
  - url: https://api.example.edu/v1
paths:
  /vacancies:
    get:
      summary: Получить список вакансий
      responses:
        '200':
          description: Список вакансий
    post:
      summary: Создать вакансию
      responses:
        '201':
          description: Вакансия создана
  /vacancies/{vacancyId}/moderation:
    post:
      summary: Принять решение по модерации вакансии
      parameters:
        - name: vacancyId
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Решение сохранено
  /applications:
    post:
      summary: Создать отклик студента
      responses:
        '201':
          description: Отклик создан
  /applications/{applicationId}/status:
    patch:
      summary: Обновить статус отклика
      parameters:
        - name: applicationId
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Статус обновлён
  /recommendations:
    get:
      summary: Получить рекомендации вакансий для студента
      responses:
        '200':
          description: Список рекомендаций
  /interviews:
    post:
      summary: Назначить интервью
      responses:
        '201':
          description: Интервью создано
components:
  schemas:
    Vacancy:
      type: object
      properties:
        id:
          type: string
        title:
          type: string
        status:
          type: string
          enum: [DRAFT, MODERATION, PUBLISHED, REJECTED, CLOSED]
    Application:
      type: object
      properties:
        id:
          type: string
        vacancyId:
          type: string
        studentId:
          type: string
        status:
          type: string
          enum: [NEW, REVIEW, INTERVIEW, OFFER, REJECTED]
    Recommendation:
      type: object
      properties:
        vacancyId:
          type: string
        score:
          type: number
        explanation:
          type: string
```

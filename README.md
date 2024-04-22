# TZCodex-Optimus-
Тестовое задание QA Manual 
 Codex Optimus 

-----------------------------------

Условия: 

1) В банковском приложении реализована бонусная система, которая рассчитывает процент скидки на обслуживание в зависимости от количества баллов, накопленных клиентом. 

2) Баллы начисляются за любые покупки, совершенные с использованием карты. За каждые 1000 рублей потраченные клиентом начисляется 1 балл. 
----------------------------------


Правила расчета скидки: 

От 0 до 150 баллов - скидка 1%;
От 150 до 200 баллов - скидка 5%;
От 200 до 400 баллов - скидка 7%;
От 400 баллов - скидка 10%;
-----------------------------------


Для работы с бонусной системой приложение использует следующие API-методы:

1) POST /api/customer/{customer_id}/purchase: Этот метод используется для начисления бонусных баллов клиенту за каждую покупку. В ответе возвращает обновленное количество бонусных баллов клиента.

2) GET /api/customer/{customer_id}/points: Этот метод возвращает текущее количество бонусных баллов для указанного клиента.

3) POST /api/discount/calculate: Этот метод принимает количество баллов в качестве параметра и возвращает процент скидки в соответствии с условиями начисления.
-----------------------------------

Задача:

Составьте список проверок, которые гарантируют, что бонусная система работает корректно.
Результат выполнения задания выложите в публичный Github-репозиторий.
Если в процессе выполнения задания возникают вопросы, укажите их в отдельном файле в репозитории.

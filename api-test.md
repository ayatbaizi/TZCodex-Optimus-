[**Общие сведения о тестировании: 3**](#общие-сведения-о-тестировании)

# Общие сведения о тестировании:

Объект тестирования:
[<u>https://osago.finuslugi.ru/</u>](https://osago.finuslugi.ru/)

Тестируемый функционал: бонусная система скидок

Сроки тестирования: 21.04.2024 - 21.04.2024

Тестирование проводилось в:

- Postman

Операционная система:

- MAC OS

**Codex Optimus**

<table>
<colgroup>
<col style="width: 4%" />
<col style="width: 8%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 12%" />
<col style="width: 26%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>ID</strong></th>
<th><strong>Приоритет</strong></th>
<th><strong><mark>Предусловия</mark></strong></th>
<th><strong><mark>Заголовок</mark></strong></th>
<th><strong>Тестовые данные</strong></th>
<th><strong>Шаги выполнения</strong></th>
<th><strong>Ожидаемый результат</strong></th>
</tr>
<tr class="odd">
<th colspan="7"><strong>Позитивные проверки</strong></th>
</tr>
<tr class="header">
<th rowspan="3">1.</th>
<th rowspan="3">high</th>
<th rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th rowspan="3"><mark>Начисление баллов клиенту за покупку</mark></th>
<th rowspan="3"><p>{customer_id} = 123</p>
<p>request body:</p>
<p>{ “amount”: 3000 }</p></th>
<th><ol type="1">
<li><p>Отправить метод POST
/api/customer/<strong>{customer_id}</strong>/purchase</p></li>
</ol></th>
<th><mark>Запрос успешно отправлен на сервер</mark></th>
</tr>
<tr class="odd">
<th><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></th>
<th>HTTP Status: 200 OK</th>
</tr>
<tr class="header">
<th><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></th>
<th><mark>В теле ответа от сервера</mark> вернулось обновленное
количество бонусных баллов клиента<mark>: 3</mark></th>
</tr>
<tr class="odd">
<th rowspan="9">2.</th>
<th rowspan="9">high</th>
<th rowspan="9"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th rowspan="9"><mark>Получение текущего количества баллов указанного
клиента</mark></th>
<th rowspan="9">{customer_id} = 123</th>
<th rowspan="2"><ol type="1">
<li><p>Отправить метод GET
/api/customer/<strong>{customer_id}</strong>/points</p></li>
</ol></th>
<th rowspan="2"><mark>Запрос успешно отправлен на сервер</mark></th>
</tr>
<tr class="header">
</tr>
<tr class="odd">
<th rowspan="3"><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></th>
<th rowspan="4">HTTP Status: 200 OK</th>
</tr>
<tr class="header">
</tr>
<tr class="odd">
</tr>
<tr class="header">
<th rowspan="4"><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></th>
</tr>
<tr class="odd">
<th rowspan="3"><mark>В теле ответа от сервера</mark> вернулось
<mark>корректное количество баллов для клиента с ID 123.</mark></th>
</tr>
<tr class="header">
</tr>
<tr class="odd">
</tr>
<tr class="header">
<th rowspan="3">3.</th>
<th rowspan="3">high</th>
<th rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th rowspan="3"><mark>Расчет скидки при количестве баллов от 0 до
149</mark></th>
<th rowspan="3"><p>request body:</p>
<p>{ “points”: 0 } или</p>
<p>{ “points”: 100 } или</p>
<p>{ “points”: 149 }</p></th>
<th><ol type="1">
<li><p>Отправить метод POST /api/discount/calculate</p></li>
</ol></th>
<th><mark>Запрос успешно отправлен на сервер</mark></th>
</tr>
<tr class="odd">
<th><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></th>
<th>HTTP Status: 200 OK</th>
</tr>
<tr class="header">
<th><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></th>
<th><mark>В теле ответа от сервера</mark> вернулось <mark>:
1%</mark></th>
</tr>
<tr class="odd">
<th rowspan="3">4.</th>
<th rowspan="3">high</th>
<th rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th rowspan="3"><mark>Расчет скидки при количестве баллов от 150 до
199</mark></th>
<th rowspan="3"><p>request body:</p>
<p>{ “points”: 150 } или</p>
<p>{ “points”: 175 } или</p>
<p>{ “points”: 199 }</p></th>
<th><ol type="1">
<li><p>Отправить метод POST /api/discount/calculate</p></li>
</ol></th>
<th><mark>Запрос успешно отправлен на сервер</mark></th>
</tr>
<tr class="header">
<th><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></th>
<th>HTTP Status: 200 OK</th>
</tr>
<tr class="odd">
<th><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></th>
<th><mark>В теле ответа от сервера</mark> вернулось <mark>:
5%</mark></th>
</tr>
<tr class="header">
<th rowspan="3">5.</th>
<th rowspan="3">high</th>
<th rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th rowspan="3"><mark>Расчет скидки при количестве баллов от 200 до
399</mark></th>
<th rowspan="3"><p>request body:</p>
<p>{ “points”: 200 } или</p>
<p>{ “points”: 299 } или</p>
<p>{ “points”: 399 }</p></th>
<th><ol type="1">
<li><p>Отправить метод POST /api/discount/calculate</p></li>
</ol></th>
<th><mark>Запрос успешно отправлен на сервер (или запрос успешно
иницирован)</mark></th>
</tr>
<tr class="odd">
<th><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></th>
<th>HTTP Status: 200 OK</th>
</tr>
<tr class="header">
<th><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></th>
<th><mark>В теле ответа от сервера</mark> вернулось <mark>:
7%.</mark></th>
</tr>
<tr class="odd">
<th rowspan="3">6.</th>
<th rowspan="3">middle</th>
<th rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th rowspan="3"><mark>Расчет скидки при количестве баллов от 400 и
больше</mark></th>
<th rowspan="3"><p>request body:</p>
<p>{ “points”: 400 } или</p>
<p>{ “points”: 401 }</p></th>
<th><ol type="1">
<li><p>Отправить метод POST /api/discount/calculate</p></li>
</ol></th>
<th><mark>Запрос успешно отправлен на сервер</mark></th>
</tr>
<tr class="header">
<th><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></th>
<th>HTTP Status: 200 OK</th>
</tr>
<tr class="odd">
<th><ol start="3" type="1">
<li><p>Проверить, что в ответе вернулась скидка 7%</p></li>
</ol></th>
<th><mark>В теле ответа от сервера</mark> вернулось <mark>:
10%</mark></th>
</tr>
<tr class="header">
<th colspan="7"><strong>Негативные тест-кейсы</strong></th>
</tr>
<tr class="odd">
<th rowspan="9">7.</th>
<th rowspan="9">middle</th>
<th rowspan="9"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th rowspan="9"><mark>Начисление баллов при нулевой сумме
покупки</mark></th>
<th rowspan="9"><p>{customer_id} = 789</p>
<p>request body:</p>
<p>{ "amount": 0 }</p></th>
<th rowspan="2"><ol type="1">
<li><p>Отправить метод POST
/api/customer/<strong>{customer_id}</strong>/purchase</p></li>
</ol></th>
<th rowspan="3"><mark>Запрос успешно отправлен на сервер</mark></th>
</tr>
<tr class="header">
</tr>
<tr class="odd">
<th rowspan="3"><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></th>
</tr>
<tr class="header">
<th rowspan="3">HTTP Status: 200 OK</th>
</tr>
<tr class="odd">
</tr>
<tr class="header">
<th rowspan="4"><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></th>
</tr>
<tr class="odd">
<th rowspan="3"><mark>Клиент не получает баллы при нулевой сумме
покупки.</mark></th>
</tr>
<tr class="header">
</tr>
<tr class="odd">
</tr>
<tr class="header">
<th rowspan="3">8.</th>
<th rowspan="3">middle</th>
<th rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th rowspan="3"><mark>Получение баллов для несуществующего
клиента</mark></th>
<th rowspan="3">{customer_id} = 999</th>
<th><ol type="1">
<li><p>Отправить метод GET
/api/customer/<strong>{customer_id}</strong>/points</p></li>
</ol></th>
<th><mark>Запрос отправлен на сервер</mark></th>
</tr>
<tr class="odd">
<th><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></th>
<th>HTTP Status: <mark>404 (Not Found)</mark></th>
</tr>
<tr class="header">
<th><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></th>
<th><p><mark>В теле ответа от сервера</mark> вернулось<mark>:</mark></p>
<p><mark>{</mark></p>
<p><mark>"timestamp": "2024-04-21T14:53:19.321+00:00",</mark></p>
<p><mark>"status": 404,</mark></p>
<p><mark>"error": "Not Found",</mark></p>
<p><mark>"path": "</mark>/api/customer/999/points<mark>"</mark></p>
<p><mark>}</mark></p></th>
</tr>
<tr class="odd">
<th rowspan="3">9.</th>
<th rowspan="3">middle</th>
<th rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th rowspan="3"><mark>Начисление баллов при отрицательной сумме
покупки</mark></th>
<th rowspan="3"><p>{customer_id} = 456</p>
<p>request body:</p>
<p>{ “amount”: -200 }</p></th>
<th><ol type="1">
<li><p>Отправить метод POST
/api/customer/<strong>{customer_id}</strong>/purchase</p></li>
</ol></th>
<th><mark>Запрос отправлен на сервер</mark></th>
</tr>
<tr class="header">
<th><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></th>
<th><mark>"HTTP Status: 400 Bad Request</mark></th>
</tr>
<tr class="odd">
<th><ol start="3" type="1">
<li><p>Проверить, что в ответе вернулась ошибка.</p></li>
</ol></th>
<th><p><mark>В теле ответа от сервера</mark> вернулось<mark>:</mark></p>
<p><mark>{</mark></p>
<p><mark>"timestamp": "2024-04-21T15:02:16.962+00:00",</mark></p>
<p><mark>"status": 400,</mark></p>
<p><mark>"error": "Bad Request",</mark></p>
<p><mark>"path":
"</mark>/api/customer/{customer_id}/purchase<mark>"</mark></p>
<p><mark>}</mark></p></th>
</tr>
<tr class="header">
<th>10.</th>
<th></th>
<th><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/XML</mark></p>
<p><mark>Accept: application/json</mark></p></th>
<th><mark>Вызов метода POST Начисление баллов клиенту за покупку c телом
JSON и c content-type = XML</mark></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

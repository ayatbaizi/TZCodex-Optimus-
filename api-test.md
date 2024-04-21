# Общие сведения о тестировании:

Объект тестирования: API - Бонусная система скидок

Сроки тестирования: 21.04.2024 - 21.04.2024

Тестирование проводилось в:

- Postman

Операционная система:

- MAC OS

**Тест - кейсы**

<table>
<colgroup>
<col style="width: 4%" />
<col style="width: 8%" />
<col style="width: 10%" />
<col style="width: 10%" />
<col style="width: 12%" />
<col style="width: 21%" />
<col style="width: 32%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>ID</strong></td>
<td><strong>Приоритет</strong></td>
<td><strong><mark>Предусловия</mark></strong></td>
<td><strong><mark>Заголовок</mark></strong></td>
<td><strong>Тестовые данные</strong></td>
<td><strong>Шаги выполнения</strong></td>
<td><strong>Ожидаемый результат</strong></td>
</tr>
<tr class="even">
<td colspan="7"><strong>Позитивные проверки</strong></td>
</tr>
<tr class="odd">
<td rowspan="3">1.</td>
<td rowspan="3">high</td>
<td rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td rowspan="3"><mark>Начисление баллов клиенту за покупку</mark></td>
<td rowspan="3"><p>{customer_id} = 123</p>
<p>request body:</p>
<p>{ “amount”: 3000 }</p></td>
<td><ol type="1">
<li><p>Отправить метод POST
/api/customer/<strong>{customer_id}</strong>/purchase</p></li>
</ol></td>
<td><mark>Запрос успешно отправлен на сервер</mark></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></td>
<td>HTTP Status: 200 OK</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></td>
<td><mark>В теле ответа от сервера</mark> вернулось обновленное
количество бонусных баллов клиента<mark>: 3</mark></td>
</tr>
<tr class="even">
<td rowspan="4">2.</td>
<td rowspan="4">high</td>
<td rowspan="4"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td rowspan="4"><mark>Получение текущего количества баллов указанного
клиента</mark></td>
<td rowspan="4">{customer_id} = 123</td>
<td rowspan="2"><ol type="1">
<li><p>Отправить метод GET
/api/customer/<strong>{customer_id}</strong>/points</p></li>
</ol></td>
<td rowspan="2"><mark>Запрос успешно отправлен на сервер</mark></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></td>
<td>HTTP Status: 200 OK</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></td>
<td><mark>В теле ответа от сервера</mark> вернулось <mark>корректное
количество баллов для клиента с ID 123.</mark></td>
</tr>
<tr class="even">
<td rowspan="3">3.</td>
<td rowspan="3">high</td>
<td rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td rowspan="3"><mark>Расчет скидки при количестве баллов от 0 до
149</mark></td>
<td rowspan="3"><p>request body:</p>
<p>{ “points”: 0 } или</p>
<p>{ “points”: 100 } или</p>
<p>{ “points”: 149 }</p></td>
<td><ol type="1">
<li><p>Отправить метод POST /api/discount/calculate</p></li>
</ol></td>
<td><mark>Запрос успешно отправлен на сервер</mark></td>
</tr>
<tr class="odd">
<td><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></td>
<td>HTTP Status: 200 OK</td>
</tr>
<tr class="even">
<td><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></td>
<td><mark>В теле ответа от сервера</mark> вернулось <mark>:
1%</mark></td>
</tr>
<tr class="odd">
<td rowspan="3">4.</td>
<td rowspan="3">high</td>
<td rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td rowspan="3"><mark>Расчет скидки при количестве баллов от 150 до
199</mark></td>
<td rowspan="3"><p>request body:</p>
<p>{ “points”: 150 } или</p>
<p>{ “points”: 175 } или</p>
<p>{ “points”: 199 }</p></td>
<td><ol type="1">
<li><p>Отправить метод POST /api/discount/calculate</p></li>
</ol></td>
<td><mark>Запрос успешно отправлен на сервер</mark></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></td>
<td>HTTP Status: 200 OK</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></td>
<td><mark>В теле ответа от сервера</mark> вернулось <mark>:
5%</mark></td>
</tr>
<tr class="even">
<td rowspan="3">5.</td>
<td rowspan="3">high</td>
<td rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td rowspan="3"><mark>Расчет скидки при количестве баллов от 200 до
399</mark></td>
<td rowspan="3"><p>request body:</p>
<p>{ “points”: 200 } или</p>
<p>{ “points”: 299 } или</p>
<p>{ “points”: 399 }</p></td>
<td><ol type="1">
<li><p>Отправить метод POST /api/discount/calculate</p></li>
</ol></td>
<td><mark>Запрос успешно отправлен на сервер (или запрос успешно
иницирован)</mark></td>
</tr>
<tr class="odd">
<td><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></td>
<td>HTTP Status: 200 OK</td>
</tr>
<tr class="even">
<td><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></td>
<td><mark>В теле ответа от сервера</mark> вернулось <mark>:
7%.</mark></td>
</tr>
<tr class="odd">
<td rowspan="3">6.</td>
<td rowspan="3">middle</td>
<td rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td rowspan="3"><mark>Расчет скидки при количестве баллов от 400 и
больше</mark></td>
<td rowspan="3"><p>request body:</p>
<p>{ “points”: 400 } или</p>
<p>{ “points”: 401 }</p></td>
<td><ol type="1">
<li><p>Отправить метод POST /api/discount/calculate</p></li>
</ol></td>
<td><mark>Запрос успешно отправлен на сервер</mark></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></td>
<td>HTTP Status: 200 OK</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li><p>Проверить, что в ответе вернулась скидка 7%</p></li>
</ol></td>
<td><mark>В теле ответа от сервера</mark> вернулось <mark>:
10%</mark></td>
</tr>
<tr class="even">
<td colspan="7"><strong>Негативные тест-кейсы</strong></td>
</tr>
<tr class="odd">
<td rowspan="9">7.</td>
<td rowspan="9">middle</td>
<td rowspan="9"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td rowspan="9"><mark>Начисление баллов при нулевой сумме
покупки</mark></td>
<td rowspan="9"><p>{customer_id} = 789</p>
<p>request body:</p>
<p>{ "amount": 0 }</p></td>
<td rowspan="2"><ol type="1">
<li><p>Отправить метод POST
/api/customer/<strong>{customer_id}</strong>/purchase</p></li>
</ol></td>
<td rowspan="3"><mark>Запрос успешно отправлен на сервер</mark></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
<td rowspan="3"><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></td>
</tr>
<tr class="even">
<td rowspan="3">HTTP Status: 200 OK</td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
<td rowspan="4"><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></td>
</tr>
<tr class="odd">
<td rowspan="3"><mark>Клиент не получает баллы при нулевой сумме
покупки.</mark></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
<td rowspan="3">8.</td>
<td rowspan="3">middle</td>
<td rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td rowspan="3"><mark>Получение баллов для несуществующего
клиента</mark></td>
<td rowspan="3">{customer_id} = 999</td>
<td><ol type="1">
<li><p>Отправить метод GET
/api/customer/<strong>{customer_id}</strong>/points</p></li>
</ol></td>
<td><mark>Запрос отправлен на сервер</mark></td>
</tr>
<tr class="odd">
<td><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></td>
<td>HTTP Status: <mark>404 (Not Found)</mark></td>
</tr>
<tr class="even">
<td><ol start="3" type="1">
<li><p>Проверить тело ответа от сервера</p></li>
</ol></td>
<td><p><mark>В теле ответа от сервера</mark> вернулось<mark>:</mark></p>
<p><mark>{</mark></p>
<p><mark>"timestamp": "2024-04-21T14:53:19.321+00:00",</mark></p>
<p><mark>"status": 404,</mark></p>
<p><mark>"error": "Not Found",</mark></p>
<p><mark>"path": "</mark>/api/customer/999/points<mark>"</mark></p>
<p><mark>}</mark></p></td>
</tr>
<tr class="odd">
<td rowspan="3">9.</td>
<td rowspan="3">middle</td>
<td rowspan="3"><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/json</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td rowspan="3"><mark>Начисление баллов при отрицательной сумме
покупки</mark></td>
<td rowspan="3"><p>{customer_id} = 456</p>
<p>request body:</p>
<p>{ “amount”: -200 }</p></td>
<td><ol type="1">
<li><p>Отправить метод POST
/api/customer/<strong>{customer_id}</strong>/purchase</p></li>
</ol></td>
<td><mark>Запрос отправлен на сервер</mark></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li><p>Проверить код состояния</p></li>
</ol></td>
<td><mark>"HTTP Status: 400 Bad Request</mark></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li><p>Проверить, что в ответе вернулась ошибка.</p></li>
</ol></td>
<td><p><mark>В теле ответа от сервера</mark> вернулось<mark>:</mark></p>
<p><mark>{</mark></p>
<p><mark>"timestamp": "2024-04-21T15:02:16.962+00:00",</mark></p>
<p><mark>"status": 400,</mark></p>
<p><mark>"error": "Bad Request",</mark></p>
<p><mark>"path":
"</mark>/api/customer/{customer_id}/purchase<mark>"</mark></p>
<p><mark>}</mark></p></td>
</tr>
<tr class="even">
<td>10.</td>
<td></td>
<td><p><mark>Headers request:</mark></p>
<p><mark>Content-Type: application/XML</mark></p>
<p><mark>Accept: application/json</mark></p></td>
<td><mark>Вызов метода POST Начисление баллов клиенту за покупку c телом
JSON и c content-type = XML</mark></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

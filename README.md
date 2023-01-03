# Что такое веб-сервисы и как они используются

Чтобы запустить веб-сервис, который понравится пользователям, надо знать, как он работает. Это поможет стартапу правильно ставить задачу разработчикам, контролировать их работу, да и вообще понимать, что нужно именно вашему стартапу. Разбираемся, что такое веб-сервис и как стартаперу его запустить.

## Веб-сервис или веб-сайт?
Начнем с понятий. ***Веб-сервис (web-service)***— это программа в интернете, которая оказывает услугу или отвечает на определенное требование пользователя. Например, электронная почта отправляет письма, поисковик Google ищет информацию в интернете, а сайт с погодой показывает прогноз. Веб-сервис, который еще называют веб-службой — это веб-приложение.  

***Веб-сай***т — это тоже веб-приложение, но с другой функциональностью. Это страница или страницы в интернете, которые содержат информацию о чем-то. Бизнес использует оба вида веб-приложений. Например, если у вас тур-агентство, то вам подойдет и веб-сайт, и веб-сервис. Вот как между ними выбрать:

Если собираетесь размещать информацию о компании, контакты представителей, часы работы, в каких направлениях работаете, какие есть акции, то подойдет веб-сайт;
Если пользователь может не только получить информацию, но и подобрать тур на определенные даты, выбрать отель, создать учетную запись, то выбирайте  веб-сервис.
Функциональность веб-приложения зависит от его архитектуры. Как она устроена и почему важна для работы веб-сервиса?

## Как работает веб-сервис на примере банка
На самом деле, если вы не веб-разработчик и не собираетесь самостоятельно писать код для веб-приложения, то знать все протоколы и компоненты веб-приложения необязательно. Главное понимать, как работает веб-сервис. Тогда получится правильно сформулировать задачу разработчиками и проверить как она выполнена.

Разберем как работает веб-сервис на примере заявки клиента на выпуск кредитной карты в банке. Банку надо разгрузить операторов, которые формируют и обрабатывают заявки. Для этого сделали веб-приложение:

1. Пользователь заходит на сайт банка и переходит на страницу с формой заявки. Заполняет ее и нажимает «Отправить». Таким образом производится запрос на бэкенд.

2. Бэкенд обрабатывает заявку и определяет, правильно ли она заполнена. Если нет, то веб-сервис возвращает ответ клиенту, о том, что произошла ошибка. Если правильно, то он отправляет заявку в сервис управления заявками и ждет ответа.

3. Сервис управления заявками принимает или не принимает ее. Потом отправляет сообщение обратно в веб-сервис. Если заявка отклонена, то веб-сервис сообщает клиенту, что произошла ошибка. Если заявка принята, то веб-сервис передает данные брокеру сообщений.  

4. В брокере сообщений заявка встает в очередь на распределение между менеджерами. После этого клиент получает сообщение, что заявка принята и с ним свяжется менеджер.

![](https://www.purrweb.com/blog/wp-content/uploads/2022/06/3-ru-4.png.webp)

Клиент не видит пункты 2-4, так как они происходят на стороне бэкенда. Ему виден лишь результат — заявка принята или произошла ошибка. 

Хотите еще пример веб-сервиса? По ссылке ниже мы рассказываем, как за 3 месяца разработали маркетплейс для видеоконтента. В кейсе подробно описана реализация веб-сервиса, какие нюансы обсуждали с заказчиком, с какими вопросами и сложностями столкнулись и как их решили.

Информация -> [[Link]](https://www.purrweb.com/ru/blog/chto-takoe-veb-servisy-i-kak-oni-ispolzuyutsya/)

##Дипломный проект Яндекс

#1. Работа с базой данных
Задание 1
Условия:
Представь: тебе нужно проверить, отображается ли созданный заказ в базе данных.
Для этого: выведи список логинов курьеров с количеством их заказов в статусе «В доставке» (поле inDelivery = true).  
          запрос:
	  
	SELECT c.login AS "Имя", COUNT(o.id) AS "Счетчик заказов"  
	FROM "Couriers" AS c  
	JOIN "Orders" AS o ON (o."courierId" = c.id) AND o."inDelivery" = true
	GROUP BY c.login;

#Задание 2
Условия:
Ты тестируешь статусы заказов. Нужно убедиться, что в базе данных они записываются корректно.
Для этого: выведи все трекеры заказов и их статусы. 
Статусы определяются по следующему правилу:
Если поле finished == true, то вывести статус 2.
Если поле canсelled == true, то вывести статус -1.
Если поле inDelivery == true, то вывести статус 1.
Для остальных случаев вывести 0.
Технические примечания:
Доступ к базе осуществляется с помощью команды psql -U morty -d scooter_rent. Пароль: smith.
У psql есть особенность: если таблица в базе данных с большой буквы, то её в запросе нужно брать в кавычки. Например, select * from “Orders”.

           запрос:
           SELECT track AS "Номер", 
              CASE 
	        WHEN finished = true THEN 2 
	        WHEN cancelled = true THEN -1 
	        WHEN "inDelivery" = true THEN 1 
	  ELSE 0 END AS "Статус" 
          FROM "Orders";
  Для данных запросов приложены скиншоты.

#2.Автоматизация теста.

Для запуска тестов должны быть установлены пакеты pytest и requests

Для их установки можно воспользоваться любым из следующих методов:
1. используйте pip install pytest, pip install requests;
2. в PyCharm, в верхнем баре выбрать "file", в выпадающем окне "settings", раздел "project @имя проекта", python interpritator, нажать на "+" и в поисковой строке найти пакеты pytest и requests.

Для запуска теста необходимо: 
1. в файл configuration, поле "URL_SERVICE =" скопировить актуальный URL (сохраняя существующие кавычки);
2. в файле New_order.py нажать зеленый треугольник (Run 'Python tests for New_order.test.order') (правая часть верхнего бара) или комбинацией клавиш Shift+F10.
        

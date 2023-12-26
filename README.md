##Дипломный проект Яндекс

#1. Работа с базой данных
Задание 1
Условия:
Представь: тебе нужно проверить, отображается ли созданный заказ в базе данных.
Для этого: выведи список логинов курьеров с количеством их заказов в статусе «В доставке» (поле inDelivery = true).  
          запрос:
	  
	SELECT c.login AS "Имя", COUNT(o.id) AS "Счетчик заказов"  
	FROM "Couriers" AS c  
	LEFT JOIN "Orders" AS o ON c.id = o."courierId" 
	WHERE o."inDelivery" = true 
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

Для запуска теста необходимо в файл configuration скопировить актуальный URL
В файле New_order.py нажать кнопку Run 
        

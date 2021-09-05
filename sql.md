# SQL

## ÖDEV 1  
* **film** tablosunda bulunan **title** ve **description** sütunlarındaki verileri sıralayınız.  
~~~~sql
SELECT title, description FROM film;
~~~~  
* **film** tablosunda bulunan tüm sütunlardaki verileri film uzunluğu 60'tan büyük ***VE*** 75'ten küçük olma koşullarıyla sıralayınız.  
~~~~sql
SELECT * FROM film
WHERE length > 60 AND length < 75;
~~~~  
* **film** tablosunda bulunan tüm sütunlardaki verileri **rental_rate 0.99** ***VE*** **replacement_cost** 12.99 ***VEYA*** 28.99 olma koşullarıyla sıralayınız.  
~~~~sql
SELECT * FROM film
WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99;
~~~~  
* **customer** tablosunda bulunan **first_name** sütunundaki değeri 'Mary' olan müşterinin **last_name** sütunundaki değeri nedir? (*Cevap = Smith*) 
~~~~sql
SELECT last_name FROM customer
WHERE first_name = 'Mary';
~~~~  
* **film** tablosundaki uzunluğu(**length**) 50'ten büyük ***OLMAYIP*** aynı zamanda **rental_rate** değeri 2.99 veya 4.99 ***OLMAYAN*** verileri sıralayınız.  
~~~~sql
SELECT * FROM film
WHERE NOT(length > 50) AND NOT(rental_rate = 2.99 OR rental_rate = 4.99);
~~~~  
## ÖDEV 2  
* **film** tablosunda bulunan tüm sütunlardaki verileri **replacement_cost** değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız.  
~~~~sql
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
~~~~  
* **actor** tablosunda bulunan **first_name** ve **last_name** sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız.  
~~~~sql
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick', 'Ed');
~~~~  
* **film** tablosunda bulunan tüm sütunlardaki verileri **rental_rate** 0.99, 2.99, 4.99 ***VE*** **replacement_cost** 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.  
~~~~sql
SELECT * FROM film
WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
~~~~  
## ÖDEV 3  
* **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.  
~~~~sql
SELECT country FROM country
WHERE country LIKE 'A%a';
~~~~  
* **country** tablosunda bulunan **country** sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.  
~~~~sql
SELECT country FROM country
WHERE country LIKE '_____%n';
~~~~  
* **film** tablosunda bulunan **title** sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.  
~~~~sql
SELECT title FROM film
WHERE title ILIKE '%t%t%t%t%';
~~~~  
* **film** tablosunda bulunan tüm sütunlardaki verilerden **title** 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.  
~~~~sql
SELECT * FROM film
WHERE title LIKE 'C%' AND length < 90 AND rental_rate = 2.99;
~~~~  
## ÖDEV 4  
* **film** tablosunda bulunan **replacement_cost** sütununda bulunan birbirinden farklı değerleri sıralayınız.  
~~~~sql
SELECT DISTINCT replacement_cost FROM film;
~~~~  
*  **film** tablosunda bulunan **replacement_cost** sütununda birbirinden farklı kaç tane veri vardır? (*Cevap = 21*)
~~~~sql
SELECT COUNT(DISTINCT replacement_cost) FROM film;
~~~~  
* **film** tablosunda bulunan film isimlerinde (**title**) kaç tanesi T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir? (*Cevap = 9*)
~~~~sql
SELECT COUNT(*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
~~~~  
* **country** tablosunda bulunan ülke isimlerinden (**country**) kaç tanesi 5 karakterden oluşmaktadır? (*Cevap = 13*) 
~~~~sql
SELECT COUNT(*) FROM country
WHERE country LIKE '_____';
~~~~  
* **city** tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter? (*Cevap = 33*) 
~~~~sql
SELECT COUNT(*) FROM city
WHERE city ILIKE '%r';
~~~~  
## ÖDEV 5  
* **film** tablosunda bulunan ve film ismi (**title**) 'n' karakteri ile biten en uzun (**length**) 5 filmi sıralayınız.  
~~~~sql
SELECT * FROM film
WHERE title ILIKE '%n' 
ORDER BY length DESC 
LIMIT 5;
~~~~  
* **film** tablosunda bulunan ve film ismi (**title**) 'n' karakteri ile biten en kısa (**length**) ikinci 5 filmi sıralayınız.  
~~~~sql
SELECT * FROM film
WHERE title ILIKE '%n'
ORDER BY length DESC
OFFSET 5
LIMIT 5;
~~~~  
* **customer** tablosunda bulunan **last_name** sütununa göre azalan yapılan sıralamada **store_id** 1 olmak koşuluyla ilk 4 veriyi sıralayınız.  
~~~~sql
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
~~~~  
## ÖDEV 6  
* **film** tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir? (*Cevap = 2.98*)  
~~~~sql
SELECT AVG(rental_rate) FROM film;
~~~~  
*  **film** tablosunda bulunan filmlerden kaç tanesi 'C' karekteri ile başlar? (*Cevap = 92*) 
~~~~sql
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%';
~~~~  
* **film** tablosunda bulunan filmlerden **rental_rate** değeri 0.99 a eşit olan en uzun (**length**) film kaç dakikadır? (*Cevap = 184*) 
~~~~sql
SELECT length FROM film
WHERE rental_rate = 0.99
ORDER BY length DESC
LIMIT 1;
~~~~  
* **film** tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı **replacement_cost** değeri vardır? (*Cevap = 21*)  
~~~~sql
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;
~~~~  
## ÖDEV 7  
* **film** tablosunda bulunan filmleri rating değerlerine göre gruplayınız.  
~~~~sql
SELECT rating, COUNT(*) FROM film
GROUP BY rating;
~~~~  
* **film** tablosunda bulunan filmleri **replacement_cost** sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.  
~~~~sql
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
~~~~  
* **customer** tablosunda bulunan **store_id** değerlerine karşılık gelen müşteri sayılarını nelerdir?  
~~~~sql
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
~~~~  
* **city** tablosunda bulunan şehir verilerini **country_id** sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran **country_id** bilgisini ve şehir sayısını paylaşınız. (*Cevap = 60*) 
~~~~sql
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
~~~~  
## ÖDEV 8  
* **test** veritabanınızda **employee** isimli sütun bilgileri **id(INTEGER)**, **name VARCHAR(50)**, **birthday DATE**, **email VARCHAR(100)** olan bir tablo oluşturalım. 
~~~~sql
CREATE TABLE employee(
  id INTEGER,
  name VARCHAR(50),
  birthday DATE,
  email VARCHAR(100)
);
~~~~  
* Oluşturduğumuz **employee** tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.  
~~~~sql  
insert into employee (id, name, email, birthday) values (1, 'Emogene Schwandt', 'eschwandt0@jiathis.com', '1952/10/27');
insert into employee (id, name, email, birthday) values (2, 'Pepi Fardo', 'pfardo1@ycombinator.com', '1951/02/28');
insert into employee (id, name, email, birthday) values (3, 'Yehudit Fulcher', 'yfulcher2@nih.gov', '1958/12/01');
insert into employee (id, name, email, birthday) values (4, 'Adams Houtby', 'ahoutby3@oaic.gov.au', '2001/11/14');
insert into employee (id, name, email, birthday) values (5, 'Brion Regnard', 'bregnard4@google.cn', '1987/06/20');
insert into employee (id, name, email, birthday) values (6, 'Anatol Gaine', 'againe5@census.gov', '2003/07/16');
insert into employee (id, name, email, birthday) values (7, 'Bunni Hartfield', 'bhartfield6@merriam-webster.com', '1983/09/21');
insert into employee (id, name, email, birthday) values (8, 'Brena Penhalurick', 'bpenhalurick7@yellowpages.com', '1975/10/29');
insert into employee (id, name, email, birthday) values (9, 'Alma Ticic', 'aticic8@cmu.edu', '1954/01/27');
insert into employee (id, name, email, birthday) values (10, 'Nessie Torel', 'ntorel9@vkontakte.ru', '1969/11/13');
insert into employee (id, name, email, birthday) values (11, 'Granger Greswell', 'ggreswella@sogou.com', '1972/06/12');
insert into employee (id, name, email, birthday) values (12, 'Nertie Scholes', 'nscholesb@amazonaws.com', '1973/10/28');
insert into employee (id, name, email, birthday) values (13, 'Helen-elizabeth Melross', 'hmelrossc@weibo.com', '2003/02/27');
insert into employee (id, name, email, birthday) values (14, 'Jamie Antonsen', 'jantonsend@delicious.com', '1985/03/20');
insert into employee (id, name, email, birthday) values (15, 'Inness Von Welldun', 'ivone@list-manage.com', '1961/08/08');
insert into employee (id, name, email, birthday) values (16, 'Leo Pfaff', 'lpfafff@nih.gov', '1964/06/06');
insert into employee (id, name, email, birthday) values (17, 'Si Hachette', 'shachetteg@house.gov', '1997/10/22');
insert into employee (id, name, email, birthday) values (18, 'Leonora Kloska', 'lkloskah@bbb.org', '1972/02/09');
insert into employee (id, name, email, birthday) values (19, 'Rakel Breedy', 'rbreedyi@bandcamp.com', '1979/05/13');
insert into employee (id, name, email, birthday) values (20, 'Lonni Burg', 'lburgj@time.com', '1966/02/18');
insert into employee (id, name, email, birthday) values (21, 'Gasper Pressman', 'gpressmank@fc2.com', '1990/08/23');
insert into employee (id, name, email, birthday) values (22, 'Chrissie Goulborne', 'cgoulbornel@vistaprint.com', '1993/03/11');
insert into employee (id, name, email, birthday) values (23, 'Judas Annand', 'jannandm@hhs.gov', '1970/12/16');
insert into employee (id, name, email, birthday) values (24, 'Wilbert Ebanks', 'webanksn@cyberchimps.com', '1954/12/05');
insert into employee (id, name, email, birthday) values (25, 'Jens Gristock', 'jgristocko@dailymotion.com', null);
insert into employee (id, name, email, birthday) values (26, 'Travers Learmouth', 'tlearmouthp@microsoft.com', '1985/09/10');
insert into employee (id, name, email, birthday) values (27, 'Ashien Birch', 'abirchq@wix.com', '1951/10/26');
insert into employee (id, name, email, birthday) values (28, 'Celisse Yushin', 'cyushinr@mtv.com', '1980/11/08');
insert into employee (id, name, email, birthday) values (29, 'Tibold Marjoribanks', 'tmarjoribankss@businessinsider.com', '1991/01/10');
insert into employee (id, name, email, birthday) values (30, 'Sharai Prestidge', 'sprestidget@google.ca', '1992/02/14');
insert into employee (id, name, email, birthday) values (31, 'Marney Hastin', 'mhastinu@ehow.com', '2003/02/18');
insert into employee (id, name, email, birthday) values (32, 'Mathe de Keep', 'mdev@arstechnica.com', '1994/07/28');
insert into employee (id, name, email, birthday) values (33, 'Vin Patriskson', 'vpatrisksonw@omniture.com', '1975/02/27');
insert into employee (id, name, email, birthday) values (34, 'Donny Thecham', 'dthechamx@eventbrite.com', '1970/11/10');
insert into employee (id, name, email, birthday) values (35, 'Holly Tommis', 'htommisy@theatlantic.com', '1950/01/08');
insert into employee (id, name, email, birthday) values (36, 'Jonathan Prestidge', 'jprestidgez@theglobeandmail.com', '1985/02/17');
insert into employee (id, name, email, birthday) values (37, 'Rollins Heighway', 'rheighway10@npr.org', '1970/08/08');
insert into employee (id, name, email, birthday) values (38, 'Reamonn Junes', 'rjunes11@stumbleupon.com', '2003/07/23');
insert into employee (id, name, email, birthday) values (39, 'Tansy Sherrocks', 'tsherrocks12@yellowbook.com', '1984/01/29');
insert into employee (id, name, email, birthday) values (40, 'Craggie Calver', 'ccalver13@netvibes.com', '1992/04/12');
insert into employee (id, name, email, birthday) values (41, 'Shandee MacCaffery', 'smaccaffery14@forbes.com', '1971/12/26');
insert into employee (id, name, email, birthday) values (42, 'Denys Buxton', 'dbuxton15@ucla.edu', '1990/08/24');
insert into employee (id, name, email, birthday) values (43, 'Marietta Larkcum', 'mlarkcum16@mysql.com', '1969/05/26');
insert into employee (id, name, email, birthday) values (44, 'Antonella Greenrodd', 'agreenrodd17@diigo.com', '2003/02/07');
insert into employee (id, name, email, birthday) values (45, 'Nil Button', 'nbutton18@usnews.com', '1982/02/08');
insert into employee (id, name, email, birthday) values (46, 'Devy Nellis', 'dnellis19@bluehost.com', null);
insert into employee (id, name, email, birthday) values (47, 'Eleen Craw', 'ecraw1a@ebay.co.uk', '1991/07/15');
insert into employee (id, name, email, birthday) values (48, 'Titus Cheeseman', 'tcheeseman1b@php.net', '1974/03/26');
insert into employee (id, name, email, birthday) values (49, 'Jocelyn O''Caine', 'jocaine1c@hugedomains.com', '1952/11/26');
insert into employee (id, name, email, birthday) values (50, 'Flori Puddicombe', 'fpuddicombe1d@rambler.ru', '1975/06/03');
~~~~  
* Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.  
~~~~sql
UPDATE employee
SET name = 'Adam Smith' 
WHERE id = 4
RETURNING *;

UPDATE employee
SET birthday = '1978-01-01' 
WHERE name = 'Denys Buxton'
RETURNING *;

UPDATE employee
SET email = 'ccalver14@forbes.co.uk' 
WHERE id = 40
RETURNING *;

UPDATE employee
SET name = 'Vin Patrick',
	birthday = '1999-03-03',
	email = 'Pat_vin@amazon.de'
WHERE name = 'Vin Patriskson'
RETURNING *;
 
UPDATE employee
SET name = 'XXXX'
WHERE name LIKE 'B%'
RETURNING *;
~~~~  
* Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.  
~~~~sql
DELETE FROM employee
WHERE id = 6
RETURNING *;

DELETE FROM employee
WHERE name LIKE 'N%'
RETURNING *;

DELETE FROM employee
WHERE birthday = NULL
RETURNING *;

DELETE FROM employee
WHERE id between 12 AND 19
RETURNING *;

DELETE FROM employee
WHERE email ILIKE '%.com'
RETURNING *;
~~~~  
## ÖDEV 9  
* **city** tablosu ile **country** tablosunda bulunan şehir (**city**) ve ülke (**country**) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.  
~~~~sql
SELECT country, city.city FROM country
INNER JOIN city ON city.country_id = country.country_id; 
~~~~  
* **customer** tablosu ile payment tablosunda bulunan **payment_id** ile customer tablosundaki **first_name** ve **last_name** isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.  
~~~~sql
SELECT first_name, last_name, payment.payment_id FROM customer
INNER JOIN payment ON payment.customer_id = customer.customer_id;
~~~~  
* **customer** tablosu ile rental tablosunda bulunan **rental_id** ile customer tablosundaki **first_name** ve **last_name** isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.  
~~~~sql
SELECT first_name, last_name, rental.rental_id FROM customer
INNER JOIN rental ON rental.customer_id = customer.customer_id;
~~~~
## ÖDEV 10  
* **city** tablosu ile **country** tablosunda bulunan şehir (**city**) ve ülke (**country**) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
~~~~sql
SELECT city, country FROM city
LEFT JOIN country ON city.country_id = country.country_id;
~~~~  
* **customer** tablosu ile **payment** tablosunda bulunan **payment_id** ile customer tablosundaki **first_name** ve **last_name** isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.  
~~~~sql
SELECT payment.payment_id, first_name, last_name FROM customer
RIGHT JOIN payment ON payment.customer_id = customer.customer_id;
~~~~  
* **customer** tablosu ile **rental** tablosunda bulunan **rental_id** ile customer tablosundaki **first_name** ve **last_name** isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.  
~~~~sql
SELECT rental.rental_id, first_name, last_name FROM customer
FULL JOIN rental ON rental.customer_id = customer.customer_id;
~~~~
## ÖDEV 11  
* **actor** ve **customer** tablolarında bulunan **first_name** sütunları için tüm verileri sıralayalım.  
~~~~sql
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);
~~~~  
* **actor** ve **customer** tablolarında bulunan **first_name** sütunları için kesişen verileri sıralayalım.  
~~~~sql
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);
~~~~  
* **actor** ve **customer** tablolarında bulunan **first_name** sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.  
~~~~sql
(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM customer);
~~~~  
* İlk 3 sorguyu tekrar eden veriler için de yapalım.  
~~~~sql
(SELECT first_name FROM actor)
UNION ALL 
(SELECT first_name FROM customer);  

(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);  

(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);
~~~~


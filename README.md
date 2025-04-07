ЗАДАНИЕ 1
![01](https://github.com/user-attachments/assets/d2610024-c72d-4c58-abb2-7580045b6c7e)

[Uploading SQLQuery16.sql…]() 
 CREATE PROCEDURE vsavin_join_proc
 
 AS CREATE TABLE ##vsavin (
 
    first_name varchar(20),

    last_name varchar(20),

    birthday_date date,

    session_date datetime
    
 )

 INSERT INTO ##vsavin (first_name, last_name, birthday_date, session_date)
 
 VALUES ('Vladimir', 'Savin', '1987-05-29', CURRENT_TIMESTAMP)

  DECLARE @vsavin_var TABLE (
  
    first_name varchar(20),

    course_date_start date,

	random_number integer
 
 );

 INSERT INTO @vsavin_var
 
 VALUES ('Vladimir', '2025-02-25', FLOOR(1 + RAND() * 1000));

 SELECT *
 
 FROM ##vsavin
 
 JOIN @vsavin_var v ON ##vsavin.first_name = v.first_name;

 

EXEC vsavin_join_proc;
 
DROP PROCEDURE vsavin_join_proc;






 DROP TABLE ##vsavin;


 SELECT *
 
 FROM ##vsavin

TRUNCATE TABLE ##vsavin;

ЗАДАНИЕ 2

![Снимок](https://github.com/user-attachments/assets/0a798684-e841-4bf9-a90f-5d27a0514b18)

[Uploading SQL
CREATE PROCEDURE vsavin_endyear_counter_proc

AS SELECT DATEDIFF(day, GETDATE() , '2025-12-31') AS ��������_����



EXEC vsavin_endyear_counter_proc;

DROP PROCEDURE vsavin_endyear_counter_proc;Query18.sql…]()


![02](https://github.com/user-attachments/assets/38c108c5-6968-4df1-a622-651486612c1d)

[Uploading SQLQuery21.sql…]

CREATE PROCEDURE vsavin_endyear_counter_proc

AS

BEGIN

  DECLARE @now DATE;
  
	DECLARE @end DATE;
 
	DECLARE @ostatok INT;
 
	SET @end = '2025-12-31';
 
	SET @now = GETDATE();
 
	SET @ostatok = DATEDIFF(DAY, @now, @end);
 
	SELECT @ostatok AS '�������� ����'
 
	END;
	
	
	EXEC vsavin_endyear_counter_proc;

	DROP PROCEDURE vsavin_endyear_counter_proc;
()

ЗАДАНИЕ 3

![Снимок](https://github.com/user-attachments/assets/1302a7eb-fd52-4a3d-b78e-c3efb7ed2ecd)

[Uploading SQLQuery

CREATE VIEW vsavinview AS

SELECT DISTINCT order_id

FROM EDU.orders_products

WHERE order_id < 5;


SELECT *

FROM vsavinview;

DROP VIEW vsavinview;19.sql…]()

ЗАДАНИЕ 4

![Снимок](https://github.com/user-attachments/assets/a6e0cce8-71c5-41fc-90ee-353f710108c9)

[Uploading SQL

DECLARE @vsavin TABLE(

    id INT,
    
	date DATETIME
 
);


INSERT INTO @vsavin (id, date)

VALUES

(1, CURRENT_TIMESTAMP),

(2, CURRENT_TIMESTAMP + 1),

(3, CURRENT_TIMESTAMP + 2),

(4, CURRENT_TIMESTAMP + 3),

(5, CURRENT_TIMESTAMP + 4)

DECLARE vsavin_cursor CURSOR FOR

SELECT id, date

FROM @vsavin

DECLARE @id INT;

DECLARE @date DATETIME;

OPEN vsavin_cursor;

FETCH NEXT FROM vsavin_cursor INTO @id, @date;

WHILE @@FETCH_STATUS = 0
BEGIN

    UPDATE @vsavin
    
	SET id = @id + 10
 
	WHERE CURRENT OF vsavin_cursor;

	FETCH NEXT FROM vsavin_cursor INTO @id, @date;
 
END;

CLOSE vsavin_cursor;

DEALLOCATE vsavin_cursor;

SELECT * FROM @vsavin

SELECT *

FROM @vsavin;Query20.sql…]()


ЗАДАНИЕ 5

![Снимок](https://github.com/user-attachments/assets/fa73b94e-6ea6-4899-8e1f-49d904c6e978)

[Uploading 
CREATE PROCEDURE vsavin_upper_lower_converter_proc

@input VARCHAR(20)

AS

BEGIN

 DECLARE @preobrazovanie VARCHAR(20);
 
 IF ASCII(LEFT(@input, 1)) BETWEEN ASCII('A') AND ASCII('Z')
 
 BEGIN
 
  SET @preobrazovanie = UPPER(@input);
  
  END
  
  ELSE
  
 BEGIN
 
  SET @preobrazovanie = LOWER(@input);
  
 END
 
SELECT @preobrazovanie AS '���������';

END;

EXEC vsavin_upper_lower_converter_proc 'aPplE';

EXEC vsavin_upper_lower_converter_proc 'apple';

EXEC vsavin_upper_lower_converter_proc 'Apple';

DROP PROCEDURE vsavin_upper_lower_converter_proc;SQLQuery22.sql…]()







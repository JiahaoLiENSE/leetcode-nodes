---


---

<h2 id="introduction--installation">Introduction &amp; Installation</h2>
<p><a href="https://www.postgresql.org/about/">About</a><br>
<a href="https://postgresapp.com/">Postgres App for Mac</a><br>
<a href="https://www.postgresql.org/download/windows/">Postgres App for Windows</a></p>
<h2 id="commands">Commands</h2>
<p>Set up psql command in Mac:<br>
<code>vim .zshrc</code><br>
Added line (the path can be found at Postgres Dashboard GUI):<br>
<code>export PATH=$PATH:/Applications/Postgres.app/Contents/Versions/11/bin</code><br>
Make change:<br>
<code>source .zshrc</code></p>
<h3 id="database-operations">Database Operations:</h3>
<p>To quit:<br>
<code>\q</code></p>
<p>To list all databases:<br>
<code>\l</code></p>
<p>To create database:<br>
<code>CREATE DATABASE test;</code></p>
<p>To connect database:<br>
<code>psql --help</code> for all commands<br>
<code>psql -h localhost -p 5432 -U &lt;username&gt; test</code></p>
<p>Another way to connect database:<br>
<code>psql</code><br>
<code>\c test</code></p>
<p>To delete database:<br>
<code>DROP DATABASE test</code><br>
<strong>Note</strong>: Make sure it is dangours. Give permission that allow to process</p>
<p>To create table:</p>
<pre><code>CREATE TABLE [IF NOT EXISTS] table_name (
   column1 datatype(length) column_contraint,
   column2 datatype(length) column_contraint,
   column3 datatype(length) column_contraint,
   table_constraints
);
</code></pre>
<p>Example:</p>
<pre><code>CREATE TABLE books (
  id              SERIAL PRIMARY KEY,
  title           VARCHAR(100) NOT NULL,
  primary_author  VARCHAR(100) NULL
);
</code></pre>
<p>To list all tables:<br>
<code>\d</code></p>
<p>To describe specific table and info:<br>
<code>\d &lt;table_name&gt;</code></p>
<p>To insert into table:<br>
<code>INSERT INTO &lt;table_name&gt; (col1,col2...) VALUE (value1, value2...);</code></p>
<p>To test and insert huge data into table:<br>
<a href="https://www.mockaroo.com/">Mockaroo to mock data</a> and download the <code>sql</code> file</p>
<p>To execute external <code>sql</code> file:<br>
<code>\i &lt;FILE_PATH&gt;</code></p>
<p>To order query:<br>
<code>SELECT * FROM &lt;table_name&gt; ORDER BY &lt;col_name&gt; ASC | DESC;</code></p>
<p>To distinct query:<br>
<code>SELECT DISTINCT &lt;col_name&gt; FROM &lt;table_name&gt; ORDER BY &lt;col_name&gt;;</code></p>
<p>To query specific info - where:<br>
<code>SELECT * FROM &lt;table_name&gt; WHERE &lt;col_name&gt; = '';</code><br>
<code>SELECT * FROM &lt;table_name&gt; WHERE &lt;col_name&gt; = '' AND &lt;col_name&gt; = '';</code><br>
<code>SELECT * FROM &lt;table_name&gt; WHERE &lt;col_name&gt; = '' AND (&lt;col_name&gt; = '' OR &lt;col_name&gt; = '');</code></p>
<p>Comparison operator:<br>
<code>&lt;, &gt;, =, &lt;=, &gt;=, &lt;&gt;</code><br>
<code>SELECT 1 = 1;</code></p>
<p>Limit &amp; Offset:<br>
<code>SELECT * FROM &lt;table_name&gt; LIMIT 5;</code> =&gt; output 5<br>
<code>SELECT * FROM &lt;table_name&gt; OFFSET 5 LIMIT 5;</code>  =&gt; skip first 5 then output 5<br>
<code>SELECT * FROM &lt;table_name&gt; OFFSET 5 FETCH FIRST 5 ROW ONLY;</code> =&gt; Skip first 5 then fetch only 5 rows from the results</p>
<p>IN:<br>
<code>SELECT * FROM &lt;table_name&gt; WHERE &lt;col_name&gt; IN ('col_name_value', 'col_name_value' , ...);</code></p>
<p>Between:<br>
<code>SELECT * FROM &lt;table_name&gt; WHERE &lt;col_name&gt; BETWEEN ' col_name_value ' AND ' col_name_value ';</code></p>
<p>Like:<br>
<code>SELECT * FROM &lt;table_name&gt; WHERE &lt;col_name&gt; LIKE '%.com';</code> =&gt; followed by .com<br>
<code>SELECT * FROM &lt;table_name&gt; WHERE &lt;col_name&gt; LIKE '%@123.com';</code> =&gt; followed by @123.com<br>
<code>SELECT * FROM &lt;table_name&gt; WHERE &lt;col_name&gt; ILIKE 'c%';</code> =&gt; output starting from c (ignore case sensity)</p>
<p>Group by:<br>
<code>SELECT &lt;col_name&gt;, COUNT(*) FROM &lt;table_name&gt; GROUP BY &lt;col_name&gt;;</code> =&gt; group up &lt;col_name&gt; and count amounts of &lt;col_name&gt;.</p>
<p>Group by having:<br>
<code>SELECT &lt;col_name&gt;, COUNT(*) FROM &lt;table_name&gt; GROUP BY &lt;col_name&gt; HAVING COUNT(*) &gt; 5;</code> =&gt; group up &lt;col_name&gt; and count amounts of &lt;col_name&gt;, but output counts larger than 5.</p>
<p>Calculate max, min, and average, sum:<br>
<code>SELECT MAX(&lt;col_name&gt;) FROM &lt;table_name&gt;;</code> =&gt; max<br>
<code>SELECT MIN(&lt;col_name&gt;) FROM &lt;table_name&gt;;</code> =&gt; min<br>
<code>SELECT AVG(&lt;col_name&gt;) FROM &lt;table_name&gt;;</code> =&gt; average<br>
<code>SELECT ROUND(AVG(&lt;col_name&gt;)) FROM &lt;table_name&gt;;</code> =&gt; round the average number without decimal<br>
<code>SELECT SUM(&lt;col_name&gt;) FROM &lt;table_name&gt;;</code> =&gt; sum up<br>
<code>SELECT &lt;col_name_1&gt;, SUM(&lt;col_name_2&gt;) FROM &lt;table_name&gt; GROUP BY &lt;col_name_1&gt;;</code> =&gt; sum up &lt;col_name_2&gt; made by &lt;col_name_1&gt;.</p>
<p>Arithmetic Operators:<br>
<code>*, /, -, +, ^, %, !</code><br>
<code>SELECT 5!;</code> =&gt; 120<br>
<code>SELECT 10 % 3;</code> =&gt; 1</p>
<p>Arithmetic Operators round and override col name:<br>
<code>SELECT id, model, price AS original_price, ROUND(price * .10, 2) AS ten_percent_discount, ROUND(price - (price * .10), 2) AS after_discount FROM car;</code> =&gt; output car id, model name, original price, 10% price, and after discount price.</p>
<p>Coalesce(合并):<br>
<code>SELECT COALESCE(email, 'Email not provided') FROM person;</code> =&gt; output empty person email as ‘Email not provided’.</p>
<p>NULLIF:<br>
<code>SELECT COALESCE(10 / NULLIF(0, 0), 0);</code> =&gt; handle division error 10 / 0; output ‘0’ instead of output error.</p>
<p>Timestamps and Date:<br>
<code>SELECT NOW();</code> =&gt; full time format<br>
<code>SELECT NOW()::DATE;</code> =&gt; only year-month-day<br>
<code>SELECT NOW()::TIME;</code> =&gt; only hour-min-sec-milisec</p>
<p>Timestamps and Date sum and subtraction:<br>
<code>SELECT NOW() - INTERVAL '10 + DAYS';</code></p>
<p>Extracting specific date fields:<br>
<code>SELECT EXTRACT(YEAR FROM NOW());</code> =&gt; extract only YEAR from  NOW().</p>
<p>Age function:<br>
<code>SELECT first_name, date_of_birth, AGE(NOW(), date_of_birth) AS age FROM person;</code> =&gt; output the person age.</p>
<p>Primary key:<br>
<code>ALTER TABLE person ADD PRIMARY KEY (id);</code> =&gt; add primary key</p>
<p>Create unique constraint:<br>
<code>ALTER TABLE person ADD CONSTRAINT unique_email_address UNIQUE (email);</code><br>
or<br>
<code>ALTER TABLE person ADD UNIQUE (email);</code> =&gt; default name</p>
<p>Check constraints:<br>
<code>ALTER TABLE person ADD CONSTRAINT gender_constraint CHECK (gender = 'Male' OR gender = 'Female');</code> =&gt; Will only allow to insert valid data (Male or Female) for gender col.</p>
<p>Delete records:<br>
<code>DELETE FROM person WHERE email = ' ';</code></p>
<p>Update records:<br>
<code>UPDATE person SET email = '' WHERE id = '';</code></p>
<p>Deal with unique/constraint element:<br>
<code>INSERT INTO person (col_1, col_2, ...) VALUES ('col_value', 'col_value', ' ... ') ON CONFLICT (id) DO UPDATE SET email = EXCLUDED.email;</code></p>
<p>Add relationship between tables:</p>
<pre><code>create table person (
	id BIGSERIAL NOT NULL PRIMARY KEY,
	...,
	car_id BIGINT REFERENCES car(id), // allow to be NULL
	UNIQUE(car_id) // one person only has one car
);
create table car (
	id BIGSERIAL NOT NULL PRIMARY KEY,
	...
);
</code></pre>
<p>Assign value to foreign key:<br>
<code>UPDATE person SET car_id = 1 WHERE id = 1;</code> =&gt; assign a car (car_id = 1) to the person (id = 1);</p>
<p>Inner Joins:<br>
<code>SELECT * FROM person JOIN car ON person.car_id = car.id;</code><br>
Nice format table command: <code>\x</code></p>
<p>Left Joins:<br>
<code>SELECT * FROM person LEFT JOIN car ON car.id = person.car_id;</code> =&gt; shows the result even the person do not have car (does not have foreign key).</p>
<p><code>SELECT * FROM person LEFT JOIN car ON car.id = person.car_id WHERE car.* IS NULL;</code> =&gt; shows people who do not have car.</p>
<p><a href="https://stackoverflow.com/questions/406294/left-join-vs-left-outer-join-in-sql-server">Graphical Joins Explaination</a><br>
<img src="https://i.stack.imgur.com/qje6o.png" alt="Graphical Joins Explaination"></p>
<p>Delete records with foreign key:<br>
Logic =&gt; delete the person <code>id</code> who has <code>car_id</code> from <code>person</code> table, and then delete the related car  <code>id</code> from <code>car</code> table.</p>
<p>Exporting query results to CSV:<br>
<code>\copy (SELECT * FROM person LEFT JOIN car ON car.id = person.car_id) TO 'FILE_PATH/results.csv' DELIMITER ',' CSV HEADER;</code></p>
<p>Serial &amp; Sequences:<br>
<code>SELECT * FROM person_id_seq;</code> =&gt; give us <code>last_value</code> &amp; <code>log_cnt</code></p>
<p><code>SELECT nextval('person_id_seq');</code> =&gt; will increase id by 1.</p>
<p><code>ALTER SEQUENCE person_id_seq RESTART WITH 10;</code> =&gt; id sequence will restart from 10.</p>
<p>Extensions:<br>
<code>SELECT * FROM pg_available_extensions;</code> =&gt; lists of all extensions that can be used.</p>
<p>UUID Data type:<br>
<code>SELECT * FROM pg_available_extensions;</code> =&gt; find <code>uuid-ossp</code>.<br>
<code>CREATE EXTENSION IF NOT EXISTS "uuid-ossp";</code> =&gt; add extension.</p>
<p><code>\df</code> =&gt; check avaliable functions for <code>uuid-ossp</code> extension.<br>
<code>SELECT uuid_generate_v4();</code> =&gt; execute random id key.</p>
<p>Using UUID as primary key:</p>
<pre><code>create table person (
	person_uid UUID NOT NULL PRIMARY KEY,
	...,
	car_uid UUID REFERENCES car(uid), // allow to be NULL
	UNIQUE(car_uid) // one person only has one car
);
create table car (
	uid UUID NOT NULL PRIMARY KEY,
	...
);

INSERT INTO person (person_uid, ...) VALUES (uuid_generate_v4(), ...)
</code></pre>


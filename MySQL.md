
# Ubuntu

    sudo apt install mysql-server
    sudo service mysql start
    sudo mysql -u root

# Konsol Temizleme

    \! clear


# Veri Tabanı

## Veri Tabanı Listesi

SHOW DATABASES;


## Oluşturmak

    CREATE DATABASE db_name;


## Silmek

    DROP DATABASE music;


## Kullanmak

    use veritabanıadı;


## Bağlanan Veritabanını Görmek

    select database();





# Tablolar

## Tabloları Görmek

    show tables;

## Tablo Silmek

    DROP TABLE IF EXISTS uyeler;

## Tablo Yapıyı Kopyalama

    SELECT * INTO WorkerClone FROM tablo_adi;





# Kolonlar

## Kolonlar ve yapıları

    show columns from TABLOADİ;

## desc

Kolonlar ve yapılarını **show columns**la görmek ile aynı sonucu verir.

    desc TABLE




# Tablo ve Kolon Oluşturmak


    create table tutorials_tbl(
                   tutorial_id INT NOT NULL AUTO_INCREMENT,
                   tutorial_title VARCHAR(100) NOT NULL,
                   tutorial_author VARCHAR(40) NOT NULL,
                   submission_date DATE,
                   PRIMARY KEY ( tutorial_id )
        );


Tek sıra halinde

    create table uyeler( isim VARCHAR(30), soyad VARCHAR(30), yas INT NOT NULL, sehir VARCHAR(30));




# Veriler

## Veri Ekleme

Kolonlara verileri ekler

    insert into uyeler (isim,soyad,yas) values ("ahmet","duran",25),("nejla","kaçan",15),("ayşe","durmaz",30);


## Güncelleme

**Genel Yapı**

    UPDATE table_name
    SET column1 = value1, column2 = value2, ...
    WHERE condition;

**Örnek**

    update uyeler set yas=40 where isim="ahmet" and sehir="İstanbul";


## Silme

    delete from uyeler where isim="x";





# Tablo Verilerini Görmek

Tüm verileri görmek için

    select * from tablo_adi

Belirli kolonları görmek için

    select kolon1,kolon2 from tablo_adi




# Where

Belirli bir eşitliğe uyanlara verir.

    select* from engines WHERE support = "YES"

## Karşılaştırmalar

<table class="ws-table-all notranslate">
<tbody><tr>
<th style="width:20%">Operator</th>
<th style="width:70%">Description</th>
</tr>
<tr>
<td>=</td>
<td>Equal to</td>
</tr>
<tr>
<td>&gt;</td>
<td>Greater than</td>
</tr>
<tr>
<td>&lt;</td>
<td>Less than</td>
</tr>
<tr>
<td>&gt;=</td>
<td>Greater than or equal to</td>
</tr>
<tr>
<td>&lt;=</td>
<td>Less than or equal to</td>
</tr>
<tr>
<td>&lt;&gt; , !=</td>
<td>Not equal to</td>
</tr>
</tbody></table>

**Not** : Bunlar aynı zamanda alfabetik değerlerle de kullanılabilir. < "m" dediğimizde m harfinden önce gelen harflerle başlayan içeriklere bakar.

    select * from engines where support < "Y";





# Like 

LIKE operatörü, bir sütunda belirtilen bir kalıbı aramak için WHERE yan tümcesinde kullanılır 

Genel Kullanım Yapısı

    SELECT sütun1, sütun2 FROM tablo_adi  WHERE sütun LIKE şablon;

<table class="table table-bordered table-hover table-striped normal table-responsive" style="width: 100%;" width="&quot;100%">
<tbody>
<tr>
<td>
<p><span style="font-weight: 400;">LIKE komutları</span></p>
</td>
<td>
<p><span style="font-weight: 400;">Açıklama</span></p>
</td>
</tr>
<tr>
<td>
<p><span style="font-weight: 400;">WHERE Soyad LIKE 'a%'</span></p>
</td>
<td>
<p><span style="font-weight: 400;">“a” ile başlayan tüm verileri bulur.</span></p>
</td>
</tr>
<tr>
<td>
<p><span style="font-weight: 400;">WHERE Soyad LIKE '%a'</span></p>
</td>
<td>
<p><span style="font-weight: 400;">“a” ile biten tüm verileri bulur.</span></p>
</td>
</tr>
<tr>
<td>
<p><span style="font-weight: 400;">WHERE Soyad LIKE '%or%'</span></p>
</td>
<td>
<p><span style="font-weight: 400;">Herhangi bir konumda “or” bulunan verileri bulur.</span></p>
</td>
</tr>
<tr>
<td>
<p><span style="font-weight: 400;">WHERE Soyad LIKE '_r%'</span></p>
</td>
<td>
<p><span style="font-weight: 400;">İkinci konumda “r” bulunan tüm verileri bulur.</span></p>
</td>
</tr>
<tr>
<td>
<p><span style="font-weight: 400;">WHERE Soyad LIKE 'a_%'</span></p>
</td>
<td>
<p><span style="font-weight: 400;">“a” ile başlayan ve en az 2 karakter uzunluğunda olan tüm verileri bulur.</span></p>
</td>
</tr>
<tr>
<td>
<p><span style="font-weight: 400;">WHERE Soyad LIKE 'a__%'</span></p>
</td>
<td>
<p><span style="font-weight: 400;">“a” ile başlayan ve en az 3 karakter uzunluğunda olan tüm verileri bulur.</span></p>
</td>
</tr>
<tr>
<td>
<p><span style="font-weight: 400;">WHERE Soyad LIKE 'a%o'</span></p>
</td>
<td>
<p><span style="font-weight: 400;">“a” ile başlayan ve “o” ile biten tüm verileri bulur.</span></p>
</td>
</tr>
</tbody>
</table>


Örneğin içerisinde **en** ifadesi geçenleri almak istersek

    select * from engines where COMMENT LIKE "%en%";







# AND, OR, NOT, XOR

Combining conditions (AND, OR, NOT, XOR)

Örneğin where yapılarında farklı sorguları birleştirmemize yararlar

<table class="table">
<tbody><tr><td>AND </td><td>&amp;&amp; </td><td>AND Operator</td></tr>
<tr><td>OR </td><td>|| </td><td>OR  Operator</td></tr>
<tr><td>NOT </td><td> ! </td><td>Negates a Value </td></tr>
<tr><td>XOR </td><td> </td><td>XOR  Operator</td></tr>
</tbody></table>

Not o şart sağlanmıyorsa yapılacak olanı yapar

Bu şekilde where işlemlerini birleştirebiliriz

    select * from engines where COMMENT LIKE "%en%" and SUPPORT < "Y";

İç içe kullanmamız gerektiğinde parantezler ile birleştirmemiz gerekiyor.

    select * from engines where (COMMENT LIKE "%en%" and SUPPORT < "Y") and ENGINE < "Z";






# Order By

Direkt kullanımda alfabeye göre ya da sayılara göre direkt küçükten büyüğe sıralama yapıyor. Bu asc olarak geçiyor. Tersine sıralamak için desc yapıyoruz.

    select * from engines order by engine;

İstersek bu sıralamadan sonra başka değere göre de kendi içerisinde sıralamasını sağlayabiliyoruz.

    select * from engines order by support,engine;

Tersine sıralamak

    select * from engines order by support ASC ,engine DESC;





# Limit

Gösterilecek olan veri sayısını limitlemeye yarar.

    select * from engines order by support ASC ,engine DESC limit 5;

Aslında şöyle de olabiliyor. İlk verdiğimiz değer kaçıncı değerden başlayacağı. Sonra verdiğimiz değer ise o değerden sonra bize kaç değer getireceği.


    select * from engines order by support ASC ,engine DESC limit 5,2;

    +--------+---------+-----------------------------------------------------------+--------------+------+------------+
    | ENGINE | SUPPORT | COMMENT                                                   | TRANSACTIONS | XA   | SAVEPOINTS |
    +--------+---------+-----------------------------------------------------------+--------------+------+------------+
    | MEMORY | YES     | Hash based, stored in memory, useful for temporary tables | NO           | NO   | NO         |
    | CSV    | YES     | CSV storage engine                                        | NO           | NO   | NO         |
    +--------+---------+-----------------------------------------------------------+--------------+------+------------+





# JOIN

Farklı tabloları birleştirebilir, kolonları yan yana getirebilir, kesişimleri alabilir, birbirinden çıkarabilir, sola sağa birleştirebilir bir yapıdır.

<img width="400" src='https://i.pinimg.com/originals/bc/0c/8b/bc0c8ba4d12051502a68bade9bba4bc5.png' />


## Right Join

İlk yazılan değer left olan değer oluyor. Böylece 2. yazılan değer üzerinde birleştirme işlemi yapıyor.

    select * from uyeler right join sehirler on uyeler.sehir = sehirler.sehir_isim;


    +---------+--------+------+-----------+------------+---------------+-------------+
    | isim    | soyad  | yas  | sehir     | sehir_isim | sehir_agirlik | sehir_durum |
    +---------+--------+------+-----------+------------+---------------+-------------+
    | ahmet   | kaya   |   40 | İstanbul  | İstanbul   |            10 | acik        |
    | neriman | duran  |   55 | Konya     | Konya      |             1 | acik        |
    | ayşe    | yilmaz |   20 | Ankara    | Ankara     |             5 | kapali      |
    | kerim   | durmaz |   25 | İzmir     | İzmir      |             7 | acik        |
    | NULL    | NULL   | NULL | NULL      | Igdir      |             2 | kapali      |
    +---------+--------+------+-----------+------------+---------------+-------------+


## Left Join

    select * from uyeler left join sehirler on uyeler.sehir = sehirler.sehir_isim;



    +---------+--------+-----+-----------+------------+---------------+-------------+
    | isim    | soyad  | yas | sehir     | sehir_isim | sehir_agirlik | sehir_durum |
    +---------+--------+-----+-----------+------------+---------------+-------------+
    | ahmet   | kaya   |  40 | İstanbul  | İstanbul   |            10 | acik        |
    | ayşe    | yilmaz |  20 | Ankara    | Ankara     |             5 | kapali      |
    | kerim   | durmaz |  25 | İzmir     | İzmir      |             7 | acik        |
    | buse    | yeşil  |  18 | Antalya   | NULL       |          NULL | NULL        |
    | neriman | duran  |  55 | Konya     | Konya      |             1 | acik        |
    +---------+--------+-----+-----------+------------+---------------+-------------+



## Inner Join


    select * from uyeler inner join sehirler on uyeler.sehir = sehirler.sehir_isim;


    +---------+--------+-----+-----------+------------+---------------+-------------+
    | isim    | soyad  | yas | sehir     | sehir_isim | sehir_agirlik | sehir_durum |
    +---------+--------+-----+-----------+------------+---------------+-------------+
    | ahmet   | kaya   |  40 | İstanbul  | İstanbul   |            10 | acik        |
    | neriman | duran  |  55 | Konya     | Konya      |             1 | acik        |
    | ayşe    | yilmaz |  20 | Ankara    | Ankara     |             5 | kapali      |
    | kerim   | durmaz |  25 | İzmir     | İzmir      |             7 | acik        |
    +---------+--------+-----+-----------+------------+---------------+-------------+



## Outer Join

<img width="400" src="https://www.ionos.com/digitalguide/fileadmin/DigitalGuide/Screenshots_2018/Outer-Join.jpg" />

(INNER) JOIN: İki tablodaki eşleşen kayıtlar için kullanılır.

LEFT (OUTER) JOIN: İki tablodaki eşleşen kayıtlar ve eşleşmeyen sol kayıtlar için kullanılır.

RIGHT (OUTER) JOIN: İki tablodaki eşleşen kayıtlar ve eşleşmeyen sağ kayıtlar için kullanılır.

FULL (OUTER) JOIN: İki tablodaki eşleşen kayıtlar ve eşleşmeyen sol ve sağ kayıtlar için kullanılır.


    select * from uyeler right outer join sehirler on uyeler.sehir = sehirler.sehir_isim;

    +---------+--------+------+-----------+------------+---------------+-------------+
    | isim    | soyad  | yas  | sehir     | sehir_isim | sehir_agirlik | sehir_durum |
    +---------+--------+------+-----------+------------+---------------+-------------+
    | ahmet   | kaya   |   40 | İstanbul  | İstanbul   |            10 | acik        |
    | neriman | duran  |   55 | Konya     | Konya      |             1 | acik        |
    | ayşe    | yilmaz |   20 | Ankara    | Ankara     |             5 | kapali      |
    | kerim   | durmaz |   25 | İzmir     | İzmir      |             7 | acik        |
    | NULL    | NULL   | NULL | NULL      | Igdir      |             2 | kapali      |
    +---------+--------+------+-----------+------------+---------------+-------------+




## Using

on x.id = y.id kullanımı yerine using ile daha kısa bir şekilde bağıntı kurabiliyoruz. Fakat burada her 2 tabloda da kolon adının aynı olması gerekiyor.

    select * from uyeler inner join sehirler USING (sehir)



## Natural Join

NATURAL JOIN : Natural join, iki tablo arasında aynı isimde olan sütunları birbiriyle otomatik olarak bağlayan bir Join türüdür.

Ortak kullanım isimlerine göre birleştirir. Risklidir.

    select * from uyeler f natural join sehirler ft;

    +---------+--------+-----+-----------+---------+------------+---------------+-------------+
    | isim    | soyad  | yas | sehir     | agirlik | sehir_isim | sehir_agirlik | sehir_durum |
    +---------+--------+-----+-----------+---------+------------+---------------+-------------+
    | ahmet   | kaya   |  40 | İstanbul  | NULL    | Igdir      |             2 | kapali      |
    | ahmet   | kaya   |  40 | İstanbul  | NULL    | İzmir      |             7 | acik        |
    | ahmet   | kaya   |  40 | İstanbul  | NULL    | Ankara     |             5 | kapali      |
    | ahmet   | kaya   |  40 | İstanbul  | NULL    | Konya      |             1 | acik        |
    | ahmet   | kaya   |  40 | İstanbul  | NULL    | İstanbul   |            10 | acik        |
    | ayşe    | yilmaz |  20 | Ankara    | NULL    | Igdir      |             2 | kapali      |
    | ayşe    | yilmaz |  20 | Ankara    | NULL    | İzmir      |             7 | acik        |
    | ayşe    | yilmaz |  20 | Ankara    | NULL    | Ankara     |             5 | kapali      |






# Aggregate

## Count

Bir yerdeki alanları ya da sayıları saymaya yarar. Toplam eleman sayısını verir, toplamı vermez.

Örneğin bir tabloda kaç veri olduğuna bakmak istersek

    select count(*) as toplam_eleman from uyeler;


    +---------------+
    | toplam_eleman |
    +---------------+
    |             5 |
    +---------------+



## Sum

Değerlerin toplamını verir.

    select sum(yas) from uyeler;

    +----------+
    | sum(yas) |
    +----------+
    |      158 |
    +----------+



## Min - Max

Bir yerdeki min ve max değerleri verir. Aynı zamanda alfabetik içeriklerde de sıralama yapabiliyor.

    select min(isim),max(yas) from uyeler;


    +-----------+----------+
    | min(isim) | max(yas) |
    +-----------+----------+
    | ahmet     |       55 |
    +-----------+----------+




## Avg

Ortalama değeri verir

    select avg(yas) from uyeler;


    +----------+
    | avg(yas) |
    +----------+
    |  31.6000 |
    +----------+




## Sorgu İçi Sorgu

Örneğin yaşı ortalamadan büyük olanları alabiliriz. Buarada sorgu içinde sorguları kullanmış oluyoruz.

    select * from uyeler where yas > (select avg(yas) from uyeler);

    +---------+-------+-----+-----------+
    | isim    | soyad | yas | sehir     |
    +---------+-------+-----+-----------+
    | ahmet   | kaya  |  40 | İstanbul  |
    | neriman | duran |  55 | Konya     |
    +---------+-------+-----+-----------+


## Distinct

Unique yapısıdır. Farklı değerleri verir. Toplam tip kavramıdır.

    select distinct(sehir) from uyeler;

    +-----------+
    | sehir     |
    +-----------+
    | İstanbul  |
    | Ankara    |
    | İzmir     |
    | Antalya   |
    | Konya     |
    +-----------+



## insert için yapı

Örneğin insert ederken bir şeyin id değeri son değerden büyük vs olması gerekebilir. Bu gibi durumlarda direkt max sorgularını kullanabiliyoruz. Örneğin eklenecek değer, listedeki en büyük yaştan 1 büyük olacak.

    INSERT INTO uyeler (yas,sehir,isim,soyad) SELECT 1 + coalesce((SELECT max(yas) FROM uyeler), 0),'İstanbul', "ahmet","arslan";




# Truncate

Tablo yapısını değiştirmeden sadece içindekileri tek bir komutla silmeyi sağlar. Tabloyu boşaltır.

    TRUNCATE TABLE uyeler;



# MySQL Data Types

## Numeric

<figure class="wp-block-table"><table><thead><tr><th>Numeric Types</th><th>Description</th></tr></thead><tbody><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-int/"><code>TINYINT</code></a></td><td>A very small integer</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-int/"><code>SMALLINT</code></a></td><td>A small integer</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-int/"><code>MEDIUMINT</code></a></td><td>A medium-sized integer</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-int/"><code>INT</code></a></td><td>A standard integer</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-int/"><code>BIGINT</code></a></td><td>A large integer</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-decimal/"><code>DECIMAL</code></a></td><td>A fixed-point number</td></tr><tr><td>&nbsp;<code>FLOAT</code></td><td>A single-precision floating point number</td></tr><tr><td>&nbsp;<code>DOUBLE</code></td><td>A double-precision floating point number</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-bit/"><code>BIT</code></a></td><td>A bit field</td></tr></tbody></table></figure>


<table aria-label="int, bigint, smallint, and tinyint (Transact-SQL)" class="table table-sm">
<thead>
<tr>
<th>Data type</th>
<th>Range</th>
<th>Storage</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>bigint</strong></td>
<td>-2^63 (-9,223,372,036,854,775,808) to 2^63-1 (9,223,372,036,854,775,807)</td>
<td>8 Bytes</td>
</tr>
<tr>
<td><strong>int</strong></td>
<td>-2^31 (-2,147,483,648) to 2^31-1 (2,147,483,647)</td>
<td>4 Bytes</td>
</tr>
<tr>
<td><strong>smallint</strong></td>
<td>-2^15 (-32,768) to 2^15-1 (32,767)</td>
<td>2 Bytes</td>
</tr>
<tr>
<td><strong>tinyint</strong></td>
<td>0 to 255</td>
<td>1 Byte</td>
</tr>
</tbody>
</table>



## Boolean

MySQL does not have the built-in BOOLEAN or BOOL data type. To represent boolean values, MySQL uses the smallest integer type which is TINYINT(1). In other words, BOOLEAN and BOOL are synonyms for TINYINT(1).

        CREATE TABLE tasks (
            id INT PRIMARY KEY AUTO_INCREMENT,
            title VARCHAR(255) NOT NULL,
            completed BOOLEAN
        );


## String

<figure class="wp-block-table"><table><thead><tr><th>String Types</th><th>Description</th></tr></thead><tbody><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-char-data-type/"><code>CHAR</code></a></td><td>A fixed-length nonbinary (character) string</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-varchar/"><code>VARCHAR</code></a></td><td>A variable-length non-binary string</td></tr><tr><td>&nbsp;<code>BINARY</code></td><td>A fixed-length binary string</td></tr><tr><td>&nbsp;<code>VARBINARY</code></td><td>A variable-length binary string</td></tr><tr><td>&nbsp;<code>TINYBLOB</code></td><td>A very small BLOB (binary large object)</td></tr><tr><td>&nbsp;<code>BLOB</code></td><td>A small BLOB</td></tr><tr><td>&nbsp;<code>MEDIUMBLOB</code></td><td>A medium-sized BLOB</td></tr><tr><td>&nbsp;<code>LONGBLOB</code></td><td>A large BLOB</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-text/"><code>TINYTEXT</code></a></td><td>A very small non-binary string</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-text/"><code>TEXT</code></a></td><td>A small non-binary string</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-text/"><code>MEDIUMTEXT</code></a></td><td>A medium-sized non-binary string</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-text/"><code>LONGTEXT</code></a></td><td>A large non-binary string</td></tr><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-enum/"><code>ENUM</code></a></td><td>An enumeration; each column value may be assigned one enumeration member</td></tr><tr><td>&nbsp;<code>SET</code></td><td>A set; each column value may be assigned zero or more <code>SET</code> members</td></tr></tbody></table></figure>





## Data and Time

<figure class="wp-block-table ref"><table><thead><tr><th>Date and Time Types</th><th>Description</th></tr></thead><tbody><tr><td>&nbsp;<a href="https://www.mysqltutorial.org/mysql-date/"><code>DATE</code></a></td><td>A date value in <code>CCYY-MM-DD</code> format</td></tr><tr><td>&nbsp;<code><a href="https://www.mysqltutorial.org/mysql-time/">TIME</a></code></td><td>A time value in <code>hh:mm:ss</code> format</td></tr><tr><td>&nbsp;<code><a href="https://www.mysqltutorial.org/mysql-datetime/">DATETIME</a></code></td><td>A date and time value in<code>CCYY-MM-DD hh:mm:ss</code>format</td></tr><tr><td>&nbsp;<code><a href="https://www.mysqltutorial.org/mysql-timestamp.aspx">TIMESTAMP</a></code></td><td>A timestamp value in <code>CCYY-MM-DD hh:mm:ss</code> format</td></tr><tr><td>&nbsp;<code>YEAR</code></td><td>A year value in <code>CCYY</code> or <code>YY </code>format</td></tr></tbody></table></figure>



## Spatial

<figure class="wp-block-table ref"><table><thead><tr><th>Spatial Data Types</th><th>Description</th></tr></thead><tbody><tr><td>&nbsp;<code>GEOMETRY</code></td><td>A spatial value of any type</td></tr><tr><td>&nbsp;<code>POINT</code></td><td>A point (a pair of X-Y coordinates)</td></tr><tr><td>&nbsp;<code>LINESTRING</code></td><td>A curve (one or more <code>POINT </code>values)</td></tr><tr><td>&nbsp;<code>POLYGON</code></td><td>A polygon</td></tr><tr><td>&nbsp;<code>GEOMETRYCOLLECTION</code></td><td>A collection of <code>GEOMETRY</code>values</td></tr><tr><td>&nbsp;<code>MULTILINESTRING</code></td><td>A collection of <code>LINESTRING</code>values</td></tr><tr><td>&nbsp;<code>MULTIPOINT</code></td><td>A collection of <code>POINT</code>values</td></tr><tr><td>&nbsp;<code>MULTIPOLYGON</code></td><td>A collection of <code>POLYGON</code>values</td></tr></tbody></table></figure>





# Primary Key

Bir tablodaki benzersiz değerlerdir. Fatura numarası gibi tekrarlanamayacak değerlerdir.

İstersek bir tablonun kolonunun oluşturulma başında belirtebiliyoruz ya da en altta belirtebiliyoruz.

    create table deneme(id_degeri int primary key);

.

    create table deneme2( id_degeri int, primary key(id_degeri));



# Auto_increment

Otomatik yükselen değişkenler oluşturmaya yarar. Bunlar boş geçilemez. Aynı zamanda primary key olmalarını ister böylece bunlar aslında id'lerdir. Kendi kendilerine eklenirler.

    create table deneme( id int not null primary key auto_increment, isim varchar(30));
    insert into deneme(isim) values("ahmet"),("ayşe");


    +----+-------+
    | id | isim  |
    +----+-------+
    |  1 | ahmet |
    |  2 | ayşe  |
    +----+-------+



# Alter

## Kolon Eklemek

Zaten olan bir tabloya kolon eklemeye yarar.

    ALTER TABLE uyeler add column kilo int;

    +-------+-------------+------+-----+---------+-------+
    | Field | Type        | Null | Key | Default | Extra |
    +-------+-------------+------+-----+---------+-------+
    | isim  | varchar(30) | YES  |     | NULL    |       |
    | soyad | varchar(30) | YES  |     | NULL    |       |
    | yas   | int         | NO   |     | NULL    |       |
    | sehir | varchar(30) | YES  |     | NULL    |       |
    | kilo  | int         | YES  |     | NULL    |       |
    +-------+-------------+------+-----+---------+-------+

Böyle eklediğimizde direkt en sona ekliyor. Bir kolondan sonra eklemesini istiyorsak After kullanabiliriz.

    alter table uyeler add column yeni varchar(20) after sehir;


    +-------+-------------+------+-----+---------+-------+
    | Field | Type        | Null | Key | Default | Extra |
    +-------+-------------+------+-----+---------+-------+
    | isim  | varchar(30) | YES  |     | NULL    |       |
    | soyad | varchar(30) | YES  |     | NULL    |       |
    | yas   | int         | NO   |     | NULL    |       |
    | sehir | varchar(30) | YES  |     | NULL    |       |
    | yeni  | varchar(20) | YES  |     | NULL    |       |
    | kilo  | int         | YES  |     | NULL    |       |
    +-------+-------------+------+-----+---------+-------+



## Kolon Silme

    alter table uyeler drop column yeni;

    +-------+-------------+------+-----+---------+-------+
    | Field | Type        | Null | Key | Default | Extra |
    +-------+-------------+------+-----+---------+-------+
    | isim  | varchar(30) | YES  |     | NULL    |       |
    | soyad | varchar(30) | YES  |     | NULL    |       |
    | yas   | int         | NO   |     | NULL    |       |
    | sehir | varchar(30) | YES  |     | NULL    |       |
    | kilo  | int         | YES  |     | NULL    |       |
    +-------+-------------+------+-----+---------+-------+



## Kolon tip değiştirme

    alter table uyeler modify column kilo varchar(10);

    +-------+-------------+------+-----+---------+-------+
    | Field | Type        | Null | Key | Default | Extra |
    +-------+-------------+------+-----+---------+-------+
    | isim  | varchar(30) | YES  |     | NULL    |       |
    | soyad | varchar(30) | YES  |     | NULL    |       |
    | yas   | int         | NO   |     | NULL    |       |
    | sehir | varchar(30) | YES  |     | NULL    |       |
    | kilo  | varchar(10) | YES  |     | NULL    |       |



## Kolon adı değiştirme

    alter table uyeler rename column kilo TO agirlik;



# As

Bir sorguda gösterilen tablo adı kısmını sadece gösterimlik bir şekilde değiştirmeye yarar. Sorgu yazarken AS olarak kullansak da tam ismi Aliases'dir.

    select max(yas) as maximum_yas from uyeler;


    +-------------+
    | maximum_yas |
    +-------------+
    |          56 |
    +-------------+



# Concat

2 string ifadeyi birleştirir ve tek bir string yapar. Gerekirse arasına başka bir karakter de elle girebiliriz.

    SELECT CONCAT (isim,"+",soyad) as adsoyad from uyeler;

    +---------------+
    | adsoyad       |
    +---------------+
    | ahmet+kaya    |
    | ayşe+yilmaz   |
    | kerim+durmaz  |
    | buse+yeşil    |
    | neriman+duran |
    | ahmet+arslan  |
    +---------------+
    
Bunu sıralama kısımlarında ya da diğer içeriklerde bile kullanabiliriz.

    SELECT CONCAT (isim,"+",soyad) as adsoyad from uyeler order by concat(isim,soyad);

    +---------------+
    | adsoyad       |
    +---------------+
    | ahmet+arslan  |
    | ahmet+kaya    |
    | ayşe+yilmaz   |
    | buse+yeşil    |
    | kerim+durmaz  |
    | neriman+duran |
    +---------------+




# Group By

GROUP BY ifadesi tabloyu veya birlikte sorgulanan tabloları gruplara bölmek için kullanılır.

Bu sorgu şehirlere göre grupladıktan sonra her şehirde kaç eleman olduğunu verir.

    select count(*) from uyeler group by sehir;

    +----------+
    | count(*) |
    +----------+
    |        2 |
    |        1 |
    |        1 |
    |        1 |
    |        1 |
    +----------+



## Having

WHERE komutu gruplama fonksiyonları ile kullanılmadığından aynı görevi yapan HAVING komutu geliştirilmiştir. Sadece GROUP BY komutu ile kullanılır.

    select sehir from uyeler group by sehir having count(*) > 1;

    +-----------+
    | sehir     |
    +-----------+
    | İstanbul  |
    +-----------+






# Union

Farklı tablolardan verileri çekip bir arada göstermeye yararlar. Farklı isimlerdeki fakat aynı türdeki kolonları bir araya getirerek diğerinin altına ekler ve ona göre bunu gösterir.

    select sehir_isim from sehirler union select isim from uyeler;

    +------------+
    | sehir_isim |
    +------------+
    | İstanbul   |
    | Konya      |
    | Ankara     |
    | İzmir      |
    | Igdir      |
    | ahmet      |
    | ayşe       |
    | kerim      |
    | buse       |
    | neriman    |
    +------------+


Union kullanınca tekrar eden değerler tekrar etmez fakat union all kullanınca değerler tekrar edebilir.

    select sehir_isim from sehirler union all select sehir from uyeler;

    +------------+
    | sehir_isim |
    +------------+
    | İstanbul   |
    | Konya      |
    | Ankara     |
    | İzmir      |
    | Igdir      |
    | İstanbul   |
    | Ankara     |
    | İzmir      |
    | Antalya    |
    | Konya      |
    | İstanbul   |
    +------------+







# any, some, all, in, not



## any

Any ile alt sorguya bakar içerisinden 1 tanesi bile True döndürse bu sefer True olan değerleri verir.

    select * from uyeler where sehir = ANY (select sehir from uyeler where yas > 40);


    +---------+--------+-----+-----------+---------+
    | isim    | soyad  | yas | sehir     | agirlik |
    +---------+--------+-----+-----------+---------+
    | ahmet   | kaya   |  40 | İstanbul  | NULL    |
    | neriman | duran  |  55 | Konya     | NULL    |
    | ahmet   | arslan |  56 | İstanbul  | NULL    |
    +---------+--------+-----+-----------+---------+


## all

Alt sorgudaki bütün değerler true değerini verirse bu durumda değerleri verir.


    select * from uyeler where sehir = ALL (select sehir from uyeler where yas > 40);


## in

IN operatörü bize sorgularımızı yazarken bir alanın içerisindeki değerleri bir değerler kümesi içerisinden çekmemize imkân sağlar.

    select * from uyeler where yas in (40,20,51,99);

    +-------+--------+-----+-----------+---------+
    | isim  | soyad  | yas | sehir     | agirlik |
    +-------+--------+-----+-----------+---------+
    | ahmet | kaya   |  40 | İstanbul  | NULL    |
    | ayşe  | yilmaz |  20 | Ankara    | NULL    |
    +-------+--------+-----+-----------+---------+



## not in

in'in tam tersi bir şekilde içinde olmayan değerleri verir

    select * from uyeler where yas not in (40,20,51,99);

    +---------+--------+-----+-----------+---------+
    | isim    | soyad  | yas | sehir     | agirlik |
    +---------+--------+-----+-----------+---------+
    | kerim   | durmaz |  25 | İzmir     | NULL    |
    | buse    | yeşil  |  18 | Antalya   | NULL    |
    | neriman | duran  |  55 | Konya     | NULL    |
    | ahmet   | arslan |  56 | İstanbul  | NULL    |
    +---------+--------+-----+-----------+---------+




## sorgu için sorgu

    select * from uyeler where sehir = any (select sehir_isim from sehirler);

    +---------+--------+-----+-----------+---------+
    | isim    | soyad  | yas | sehir     | agirlik |
    +---------+--------+-----+-----------+---------+
    | ahmet   | kaya   |  40 | İstanbul  | NULL    |
    | ayşe    | yilmaz |  20 | Ankara    | NULL    |
    | kerim   | durmaz |  25 | İzmir     | NULL    |
    | neriman | duran  |  55 | Konya     | NULL    |
    | ahmet   | arslan |  56 | İstanbul  | NULL    |
    +---------+--------+-----+-----------+---------+








# Exist ve Not Exist

EXISTS ifadesi kullanıldığında, alt sorguda istenilen şartın yerine getirildiği durumda bir üstteki sorgu değer üretir.

NOT EXISTS ifadesi ise tam tersi olarak, alt sorguda istenilen şartın sağlanmadığı durumda bir üstteki sorgu değer üretir.

    select * from uyeler where exists (select * from sehirler where uyeler.sehir = sehirler.sehir_isim);


    +---------+--------+-----+-----------+---------+
    | isim    | soyad  | yas | sehir     | agirlik |
    +---------+--------+-----+-----------+---------+
    | ahmet   | kaya   |  40 | İstanbul  | NULL    |
    | ayşe    | yilmaz |  20 | Ankara    | NULL    |
    | kerim   | durmaz |  25 | İzmir     | NULL    |
    | neriman | duran  |  55 | Konya     | NULL    |
    | ahmet   | arslan |  56 | İstanbul  | NULL    |
    +---------+--------+-----+-----------+---------+

ya da

    select * from uyeler where not exists (select * from sehirler where uyeler.sehir = sehirler.sehir_isim);

    +------+--------+-----+---------+---------+
    | isim | soyad  | yas | sehir   | agirlik |
    +------+--------+-----+---------+---------+
    | buse | yeşil  |  18 | Antalya | NULL    |
    +------+--------+-----+---------+---------+




# User Variables

Tanımlanan değişkenler MySQL içerisinde bulunan fonksiyonlarda da kullanılabilir. Bunlar silinemez, oturum kapatıldığında otomatik olarak hafızadan silinirler.

## Sabit

    set @ad := "ahmet";
    select * from uyeler where isim = @ad;

    +-------+--------+-----+-----------+---------+
    | isim  | soyad  | yas | sehir     | agirlik |
    +-------+--------+-----+-----------+---------+
    | ahmet | kaya   |  40 | İstanbul  | NULL    |
    | ahmet | arslan |  56 | İstanbul  | NULL    |
    +-------+--------+-----+-----------+---------+


## Ekrana Basma

Oluşturulmuş bir değişkeni göstermeye yarar.

    select @ad;

    +-------+
    | @ad   |
    +-------+
    | ahmet |
    +-------+





## Sorgularla

    select @test := max(yas) from uyeler;
    select @test;

    +-------+
    | @test |
    +-------+
    |    56 |
    +-------+



## Son değer mantığı

Eğer birden fazla değer sonucu gönderiyorsak bu durumda sadece son değeri alır.


    select @isimler:= isim from uyeler;
    select @isimler;

    +-----------------+
    | @isimler:= isim |
    +-----------------+
    | ahmet           |
    | ayşe            |
    | kerim           |
    | buse            |
    | neriman         |
    | ahmet           |
    +-----------------+
    
    +----------+
    | @isimler |
    +----------+
    | ahmet    |
    +----------+


## Set vs Select

Set sadece 1 değişken atayabilirken, select birden fazla değişken atayabilir. Set sadece skaler bir değer atabilir.



# abs

Sayıların mutlak değerlerini alır

    select abs(yas) from uyeler;

    +----------+
    | abs(yas) |
    +----------+
    |       40 |
    |       20 |
    |       25 |
    |       18 |
    |       55 |
    |       56 |
    +----------+


# ceil ve floor

Sayıları bir yukarı ya da bir aşağı doğru yuvarlamaya yarar.



# mod

Bir sayının başka bir sayıya bölümünden kalanı verir. Tek ve çiftleri bulmak için genel bir yoldur.

    select mod(yas,3) from uyeler;


    +------------+
    | mod(yas,3) |
    +------------+
    |          1 |
    |          2 |
    |          1 |
    |          0 |
    |          1 |
    |          2 |
    +------------+



## round

Sayıyı verilen ondalık sayısı kadar yuvarlar. Böylece ondalıktan sonra kaç basamak gösterecek vs seçebiliyoruz.

    select round (15.2525,1);

    +-------------------+
    | round (15.2525,1) |
    +-------------------+
    |              15.3 |
    +-------------------+







# DATES

## Curdate ve Current_Date

Bugünün şu anki tarihi verir. Sadece tarih verir, saat vs vermez.

    select CURDATE();

    +------------+
    | CURDATE()  |
    +------------+
    | 2022-07-09 |
    +------------+



## current_timestamp ve now

Şu anki saat ve dk ile beraber tarihi verirler.

    select current_timestamp();

    +---------------------+
    | current_timestamp() |
    +---------------------+
    | 2022-07-09 21:44:18 |
    +---------------------+

ya da

    select now();
    
    +---------------------+
    | now()               |
    +---------------------+
    | 2022-07-13 15:58:05 |
    +---------------------+



## curtime

Saat dakika ve saliseyi verir.

    select curtime();

    +-----------+
    | curtime() |
    +-----------+
    | 21:44:57  |
    +-----------+



## DAYNAME

Verilen tarihteki gün adını alır.

    select DAYNAME(CURDATE());

    +--------------------+
    | DAYNAME(CURDATE()) |
    +--------------------+
    | Saturday           |
    +--------------------+


## DAYOFMONTH

Verilen tarihte ayın kaçıncı günü olduğunu alır

    select DAYOFMONTH(CURDATE());

    +-----------------------+
    | DAYOFMONTH(CURDATE()) |
    +-----------------------+
    |                     9 |
    +-----------------------+


## DAYOFWEEK

Haftanın kaçıncı günü olduğunu verir ama saymaya 1 = Pazar ile başlar.

(1 = Sunday, 2 = Monday, …, 7 = Saturday)

    select DAYOFWEEK(CURDATE());
    +----------------------+
    | DAYOFWEEK(CURDATE()) |
    +----------------------+
    |                    7 |
    +----------------------+


## DAYOFYEAR

Yılın kaçıncı günü olduğunu verir.

    select DAYOFYEAR(CURDATE());

    +----------------------+
    | DAYOFYEAR(CURDATE()) |
    +----------------------+
    |                  190 |
    +----------------------+



## Year

Tarihten yıl kısmını alır.

    select year(curdate());

    +-----------------+
    | year(curdate()) |
    +-----------------+
    |            2022 |
    +-----------------+

## Week

Tarihten hafta kısmını alır. Kaçıncı hafta olduğunu verir.

    select week(curdate());

    +-----------------+
    | week(curdate()) |
    +-----------------+
    |              27 |
    +-----------------+


## DateDiff

2 tarih arasındaki farkı almaya yarar. Farkı bir gün yapısı olarak verir.

    select datediff(curdate(),"2021-03-11");

    +----------------------------------+
    | datediff(curdate(),"2021-03-11") |
    +----------------------------------+
    |                              485 |
    +----------------------------------+



## TIMESTAMPDIFF

Gelen değerleri başka tarihsel özelliklere çevirebiliriz. Böylece karşılaştırmalar ya da seçimlerde kullanılabilir. Örneğin 485 günün kaç yıl yaptığını hesaplayabiliriz.

    select datediff(curdate(),"2021-03-11"), TIMESTAMPDIFF(year,'2021-03-11', now() );

    +----------------------------------+------------------------------------------+
    | datediff(curdate(),"2021-03-11") | TIMESTAMPDIFF(year,'2021-03-11', now() ) |
    +----------------------------------+------------------------------------------+
    |                              485 |                                        1 |
    +----------------------------------+------------------------------------------+





## STR_TO_DATE

The STR_TO_DATE() function returns a date based on a string and a format.

https://www.w3schools.com/sql/func_mysql_str_to_date.asp#:~:text=The%20STR_TO_DATE()%20function%20returns,a%20string%20and%20a%20format

    SELECT STR_TO_DATE("2017,8,14 10,40,10", "%Y,%m,%d %h,%i,%s");

    +--------------------------------------------------------+
    | STR_TO_DATE("2017,8,14 10,40,10", "%Y,%m,%d %h,%i,%s") |
    +--------------------------------------------------------+
    | 2017-08-14 10:40:10                                    |
    +--------------------------------------------------------+



## Sorgular

Sorgularda belirli bir yıla eşit, aya eşit vs veriler almak istediğimizde içerikten o kısmı çıkarmamız ve sonrasında eşitlememiz gerekiyor.

    Select * from Worker where year(JOINING_DATE) = 2014 and month(JOINING_DATE) = 2;

    +-----------+------------+-----------+--------+---------------------+------------+
    | WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE        | DEPARTMENT |
    +-----------+------------+-----------+--------+---------------------+------------+
    |         1 | Monika     | Arora     | 100000 | 2014-02-20 09:00:00 | HR         |
    |         3 | Vishal     | Singhal   | 300000 | 2014-02-20 09:00:00 | HR         |
    |         4 | Amitabh    | Singh     | 500000 | 2014-02-20 09:00:00 | Admin      |
    +-----------+------------+-----------+--------+---------------------+------------+



# rand

    select rand();

    +---------------------+
    | rand()              |
    +---------------------+
    | 0.37541017716323044 |
    +---------------------+


# IF

IF(KOŞUL, DOĞRU, YANLIŞ) şeklinde bir yapı ile çalışır.

    SELECT IF(5 > 6, "5 büyük", "6 büyük") AS sonuc;

    +-----------+
    | sonuc     |
    +-----------+
    | 6 büyük   |
    +-----------+


Eğer yapılar içerisinde kullanırsak

    select IF(count(*)>1,"veri var","veri yok") as sonuc from uyeler where sehir = "İstanbul";
    
    +----------+
    | sonuc    |
    +----------+
    | veri var |
    +----------+


    mysql> select IF(count(*)>2,"veri var","veri yok") as sonuc from uyeler where sehir = "İstanbul";
    
    +----------+
    | sonuc    |
    +----------+
    | veri yok |
    +----------+



# Case

İf sorgularına bir alternatif olarak kullanılır. Daha rahattır. İf, elseif, else gibi kavramları içerisinde barındırır.

    select isim, 
    case WHEN yas = 40 THEN "bu 40" 
    WHEN yas > 30 then "orta" 
    ELSE "değil" end as txt 
    from uyeler;

    +---------+--------+
    | isim    | txt    |
    +---------+--------+
    | ahmet   | bu 40  |
    | ayşe    | değil  |
    | kerim   | değil  |
    | buse    | değil  |
    | neriman | orta   |
    | ahmet   | orta   |
    +---------+--------+

Tek satırda bakacak olursak

    select *, case WHEN yas = 40 THEN "bu 40" WHEN yas > 30 then "orta" ELSE "değil" end as txt from uyeler;




# REGEX

## RegExp

Direkt olarak regex yapılarını kullanabilmemizi sağlar

    select * from uyeler where isim REGEXP "^a";

    +-------+--------+-----+-----------+---------+
    | isim  | soyad  | yas | sehir     | agirlik |
    +-------+--------+-----+-----------+---------+
    | ahmet | kaya   |  40 | İstanbul  | NULL    |
    | ayşe  | yilmaz |  20 | Ankara    | NULL    |
    | ahmet | arslan |  56 | İstanbul  | NULL    |
    +-------+--------+-----+-----------+---------+
    
ya da şeklinde kullanmak için

    select * from uyeler where isim REGEXP "^a|met$";

and kullanımı

    select * from uyeler where isim REGEXP "^a" AND isim REGEXP "et$";

    +-------+--------+-----+-----------+---------+
    | isim  | soyad  | yas | sehir     | agirlik |
    +-------+--------+-----+-----------+---------+
    | ahmet | kaya   |  40 | İstanbul  | NULL    |
    | ahmet | arslan |  56 | İstanbul  | NULL    |
    +-------+--------+-----+-----------+---------+



## Not Regexp


Regex ile belirtilen kısmı karşılamayanları getirir

    select * from uyeler where isim NOT REGEXP "et$";

    +---------+--------+-----+---------+---------+
    | isim    | soyad  | yas | sehir   | agirlik |
    +---------+--------+-----+---------+---------+
    | ayşe    | yilmaz |  20 | Ankara  | NULL    |
    | kerim   | durmaz |  25 | İzmir   | NULL    |
    | buse    | yeşil  |  18 | Antalya | NULL    |
    | neriman | duran  |  55 | Konya   | NULL    |
    +---------+--------+-----+---------+---------+



## Regexp_Instr

Karşılaştığı ilk sayısal olmayan karakterin(harf ya da noktalama işareti gibi) kaçıncı karakter olduğunu yazdırmak için kullanılır

    SELECT isim, REGEXP_INSTR (isim, "r|e|o|u") as sonuc from uyeler;

    +---------+-------+
    | isim    | sonuc |
    +---------+-------+
    | ahmet   |     4 |
    | ayşe    |     4 |
    | kerim   |     2 |
    | buse    |     2 |
    | neriman |     2 |
    | ahmet   |     4 |
    +---------+-------+



## Regexp_Replace

Normal ifadeyle eşleşen alt dizeleri değiştirin. Karakterleri değiştirmeye yarar. Kalıcı değildir.

    select *,regexp_replace(isim,"a","X") from uyeler;

    +---------+--------+-----+-----------+---------+------------------------------+
    | isim    | soyad  | yas | sehir     | agirlik | regexp_replace(isim,"a","X") |
    +---------+--------+-----+-----------+---------+------------------------------+
    | ahmet   | kaya   |  40 | İstanbul  | NULL    | Xhmet                        |
    | ayşe    | yilmaz |  20 | Ankara    | NULL    | Xyşe                         |
    | kerim   | durmaz |  25 | İzmir     | NULL    | kerim                        |
    | buse    | yeşil  |  18 | Antalya   | NULL    | buse                         |
    | neriman | duran  |  55 | Konya     | NULL    | nerimXn                      |
    | ahmet   | arslan |  56 | İstanbul  | NULL    | Xhmet                        |
    +---------+--------+-----+-----------+---------+------------------------------+



## RLIKE

MySQL'deki RLIKE operatörü, kalıp eşleştirme için kullanılır. Verilen dizelerin bir normal ifadeyle eşleşip eşleşmediğini belirlemek için kullanılır . Dizeler normal ifadeyle eşleşirse 1, eşleşme bulunamazsa 0 döndürür.

Ah ile başlayanları aratıp bunlardan olanlara 1 olmayanlara 0 demesini sağlatıyoruz.

    select isim RLIKE "^ah" from uyeler;
    
    +------------------+
    | isim RLIKE "^ah" |
    +------------------+
    |                1 |
    |                0 |
    |                0 |
    |                0 |
    |                0 |
    |                1 |
    +------------------+








# Nullif

Eğer 2 ifade aynı ise null, değilse ilk ifadeyi verir.

    select nullif (1,1);

    +--------------+
    | nullif (1,1) |
    +--------------+
    |         NULL |
    +--------------+


    select nullif (1,5);

    +--------------+
    | nullif (1,5) |
    +--------------+
    |            1 |
    +--------------+


# Ifnull

Bu fonksiyonun amacı veritabanından gelen null değerini istediğimiz bir değere çevirebilmesidir.

Bir kolon adı veriyoruz eğer burada null varsa onu neyle dolduracağımızı söylüyoruz

    select *,ifnull(agirlik,10) from uyeler;

    +---------+--------+-----+-----------+---------+--------------------+
    | isim    | soyad  | yas | sehir     | agirlik | ifnull(agirlik,10) |
    +---------+--------+-----+-----------+---------+--------------------+
    | ahmet   | kaya   |  40 | İstanbul  | NULL    | 10                 |
    | ayşe    | yilmaz |  20 | Ankara    | 15      | 15                 |
    | kerim   | durmaz |  25 | İzmir     | 15      | 15                 |
    | buse    | yeşil  |  18 | Antalya   | 15      | 15                 |
    | neriman | duran  |  55 | Konya     | NULL    | 10                 |
    | ahmet   | arslan |  56 | İstanbul  | NULL    | 10                 |
    +---------+--------+-----+-----------+---------+--------------------+



# Upper and lower

Büyük ve küçük yazmak için kullanılır

    select upper(isim),lower(isim) from uyeler;

    +-------------+-------------+
    | upper(isim) | lower(isim) |
    +-------------+-------------+
    | AHMET       | ahmet       |
    | AYŞE        | ayşe        |
    | KERIM       | kerim       |
    | BUSE        | buse        |
    | NERIMAN     | neriman     |
    | AHMET       | ahmet       |
    +-------------+-------------+





# User

Geçerli MySQL kullanıcı adını verir

    select user();

    +----------------+
    | user()         |
    +----------------+
    | root@localhost |
    +----------------+


# User List

Tüm mysql kullanıcıları listesini verir

    select user from mysql.user;

    +------------------+
    | user             |
    +------------------+
    | debian-sys-maint |
    | mysql.infoschema |
    | mysql.session    |
    | mysql.sys        |
    | root             |
    +------------------+


Daha detaylı bir liste için

    select user,host,account_locked,password_expired from mysql.user;

    +------------------+-----------+----------------+------------------+
    | user             | host      | account_locked | password_expired |
    +------------------+-----------+----------------+------------------+
    | debian-sys-maint | localhost | N              | N                |
    | mysql.infoschema | localhost | Y              | N                |
    | mysql.session    | localhost | Y              | N                |
    | mysql.sys        | localhost | Y              | N                |
    | root             | localhost | N              | N                |
    +------------------+-----------+----------------+------------------+
    




# Şifre değiştirmek

    ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'new-password';




# Yedek

## Yedek Alma

Komple 

    mysqldump -u root -p --all-databases > dump.sql

Sadece bir veritabanının yedeğini almak

    mysqldump -u root -p --databases ornek > dump.sql


## Yedeği Yükleme

Öncelikle o ada sahip bir veritabanı oluşturmak gerekiyor. Yüklecek bir veritabanı oluşturuyoruz.

    create database ornek;

Sonrasında buna yükleme yapıyoruz

    mysql -u root -p ornek < dump.sql



# Status

Genel bilgiler

    mysql> status
    
    --------------
    mysql  Ver 8.0.29-0ubuntu0.20.04.3 for Linux on x86_64 ((Ubuntu))

    Connection id:          36
    Current database:       ornek
    Current user:           root@localhost
    SSL:                    Not in use
    Current pager:          stdout
    Using outfile:          ''
    Using delimiter:        ;
    Server version:         8.0.29-0ubuntu0.20.04.3 (Ubuntu)
    Protocol version:       10
    Connection:             Localhost via UNIX socket
    Server characterset:    utf8mb4
    Db     characterset:    utf8mb4
    Client characterset:    utf8mb4
    Conn.  characterset:    utf8mb4
    UNIX socket:            /var/run/mysqld/mysqld.sock
    Binary data as:         Hexadecimal
    Uptime:                 51 min 52 sec

    Threads: 2  Questions: 922  Slow queries: 0  Opens: 1727  Flush tables: 3  Open tables: 218  Queries per second avg: 0.296







# substring

Bir karakter aralığını çekip almamızı sağlar. Bir yazılı ifadenin belirli bir alanını slice etmemizi sağlar.

    Select substring(FIRST_NAME,1,3) from Worker;




# Instr

INSTR fonksiyonu parametre olarak verilen metin içerisinde, yine parametre olarak verilen metin parçasını arar ve bulduğu durumda arama sonucunun indeksini sonuç olarak geri döndürür.

    Select INSTR(FIRST_NAME, "tab") from Worker where FIRST_NAME = 'Amitabh';

    +--------------------------+
    | INSTR(FIRST_NAME, "tab") |
    +--------------------------+
    |                        4 |
    +--------------------------+




# Trim, Rtrim, Ltrim


LTRIM() fonksiyonu, dizinin baştaki tüm boşlukları ve dizinin sol tarafındaki boşlukları temizlemek için kullanılır.

RTRIM() fonksiyonu, tüm bitiş boşluklarını ve dizinin sağ tarafında yer alan tüm boşlukların temizlenmesi için kullanılır.

TRIM() fonksiyonu ile her ikisinin yaptığı işlevi yapmakla beraber çok daha fazlasını yapabilirsiniz.

    Select RTRIM(FIRST_NAME) from Worker;

    +-------------------+
    | RTRIM(FIRST_NAME) |
    +-------------------+
    | Monika            |
    | Niharika          |
    | Vishal            |
    | Amitabh           |
    | Vivek             |
    | Vipul             |
    | Satish            |
    | Geetika           |
    +-------------------+




# length

Bir string'in karakter uzunluğunu vermeye yarar.

    select length(FIRST_NAME) from Worker;

    +--------------------+
    | length(FIRST_NAME) |
    +--------------------+
    |                  6 |
    |                  8 |
    |                  6 |
    |                  7 |
    |                  5 |
    |                  5 |
    |                  6 |
    |                  7 |
    +--------------------+




# Replace

Direkt olarak karakterleri değiştirmeye yarıyor. regexp_replace ile aynı yönde ilerler. regexp_replace ile update yapmak sorun iken bunda değil.

    Select REPLACE(FIRST_NAME,'a','A') from Worker;

    +-----------------------------+
    | REPLACE(FIRST_NAME,'a','A') |
    +-----------------------------+
    | MonikA                      |
    | NihArikA                    |
    | VishAl                      |
    | AmitAbh                     |
    | Vivek                       |
    | Vipul                       |
    | SAtish                      |
    | GeetikA                     |
    +-----------------------------+

## Update

    update uyeler set isim = REPLACE(isim,"se","sa") where isim = "buse";

    mysql> select * from uyeler;
    +---------+--------+-----+-----------+---------+
    | isim    | soyad  | yas | sehir     | agirlik |
    +---------+--------+-----+-----------+---------+
    | ahmet   | kaya   |  40 | İstanbul  | NULL    |
    | ayşe    | yilmaz |  20 | Ankara    | 15      |
    | kerim   | durmaz |  25 | İzmir     | 15      |
    | busa    | yeşil  |  18 | Antalya   | 15      |
    | neriman | duran  |  55 | Konya     | NULL    |
    | ahmet   | arslan |  56 | İstanbul  | NULL    |
    +---------+--------+-----+-----------+---------+



# between

Verilen bir sayısal aralığı arar. İlk ve son değer dahildir.

    Select * from Worker where SALARY between 100000 and 500000;

    +-----------+------------+-----------+--------+---------------------+------------+
    | WORKER_ID | FIRST_NAME | LAST_NAME | SALARY | JOINING_DATE        | DEPARTMENT |
    +-----------+------------+-----------+--------+---------------------+------------+
    |         1 | Monika     | Arora     | 100000 | 2014-02-20 09:00:00 | HR         |
    |         3 | Vishal     | Singhal   | 300000 | 2014-02-20 09:00:00 | HR         |
    |         4 | Amitabh    | Singh     | 500000 | 2014-02-20 09:00:00 | Admin      |
    |         5 | Vivek      | Bhati     | 500000 | 2014-06-11 09:00:00 | Admin      |
    |         6 | Vipul      | Diwan     | 200000 | 2014-06-11 09:00:00 | Account    |
    +-----------+------------+-----------+--------+---------------------+------------+


# Düzgün Çıktı

Pretty gibi daha düzgün çıktılar için

    select * from uyeler \G;






















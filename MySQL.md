
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















































































































































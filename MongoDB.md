<img width="400" src='https://media.geeksforgeeks.org/wp-content/uploads/20200219180521/MongoDB-database-colection.png' />

# 🔴 MongoDB shell

# Database


## Listelemek

    show dbs

    admin     0.000GB
    config    0.000GB
    deneme    0.000GB
    local     0.000GB
    ornekler  0.000GB

## Oluşturma

Diğer yapılardan farklı olarak içerisine collection oluşturmadığımız sürece oluşmuş sayılmıyor.

    use deneme;

Aynı zamanda use dediğimiz zaman artık onu kullanıyor oluyoruz ve adını db olarak kısa bir şekilde kullanabiliyoruz. Yol verirken **db.collectionname** şeklinde yapıyoruz.

## Silme

Bir database içerisine use ile girdikten sonra **dropDatabase** kullanılıyor.

    db.dropDatabase()

    admin     0.000GB
    config    0.000GB
    local     0.000GB
    ornekler  0.000GB



# Konsol Temizleme

**cls**




# Collections

## Listelemek

    show collections

Aynı zamanda bir liste yapısı ile döndürmek için getCollectionNames kullanılabilir

    db.getCollectionNames()

    [ "konular", "uyeler" ]

Ya da table olarak değerlerlendirmek istersek

    show tables



## Oluşturmak

    db.createCollection("yeni")

    show collections

      konular
      uyeler
      yeni



## Silmek

    db.uyeler.drop()





# Document

## Eklemek

### insertOne

Bir tane eklemeye yarar.

    db.uyeler.insertOne({"isim":"Ahmet","yas":15,"sehir":"İstanbul"})


### insertMany

Çoklu veri eklemeyi sağlar. Bir liste şeklinde ekleme yapıyoruz.

    db.uyeler.insertMany([{"isim":"Ayşe","yas":22,"sehir":"İzmir"}, {"isim":"Kerim","yas":40,"sehir":"İstanbul"}, {"isim":"Davut","yas":40,"sehir":"Ankara"}, {"isim":"Ahmet","yas":50,"sehir":"Kanada"}])


## Silmek

### deleteOne

Sadece bir tane silmeye yarıyor. Verilen özellikte olan ilk gördüğü değeri siliyor.

    db.uyeler.deleteOne({"isim":"Ahmet"})

### deleteMany

Verilen şarta ve yapıya göre çoklu silme işlemi yapıyor.

    db.uyeler.deleteMany({"isim":"Davut"})


## Güncelleme

### updateOne

    db.uyeler.updateOne({"isim": "Ahmet"}, {$set: {price: 899}})

### updateMany

    db.deneme.updateMany({"isim": "Ahmet"}, {$set: {"price": 1000}})






























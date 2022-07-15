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





# Verileri Göstermek

Temel olarak find yapısı ile sağlanıyor. 

## findOne

Şarta ya da yapıya uygun bulduğu ilk veriyi getiriyor.

    db.uyeler.findOne()
    {
            "_id" : ObjectId("62cee0756592bf0fab88e6e0"),
            "isim" : "Ayşe",
            "yas" : 22,
            "sehir" : "İzmir"
    }


## find

Find dediğimiz zaman bize hepsini veriyor.

    db.uyeler.find()
    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 40, "sehir" : "İstanbul" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e6"), "isim" : "Kerim", "yas" : 22, "sehir" : "İzmir", "Kedi" : 0 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e7"), "isim" : "Davut", "yas" : 35, "sehir" : "Ankara", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e8"), "isim" : "Gül", "yas" : 50, "sehir" : "Muş", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e9"), "isim" : "İsmail", "yas" : 18, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6ea"), "isim" : "Mustafa", "yas" : 21, "sehir" : "İstanbul", "Kedi" : 0 }


## Temel Sorgular ve Şartlar

İçerisine şartlar alarak sadece onları getirmesini sağlayabiliriz.

    db.uyeler.find({"yas":50})
    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e8"), "isim" : "Gül", "yas" : 50, "sehir" : "Muş", "Kedi" : 1 }





# Comparison

Farklı değerlerin ve yapıların karşılaştırılması için kullanılırlar.

## $eq

Belirtilen bir değere eşit olan değerlerle eşleşir. Zaten find içerisinde belirtilen yapının temelidir.

    db.uyeler.find( { "isim": { $eq: "Ayşe"} } )
    
    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }


## $gt

Belirli bir değerden büyük olanları getirir.

    db.uyeler.find( { "yas": { $gt: 40} } )
    
    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e8"), "isim" : "Gül", "yas" : 50, "sehir" : "Muş", "Kedi" : 1 }



## $gte

Büyüktür ve eşittir anlamını verir

    db.uyeler.find( { "yas": { $gte: 40} } )
    
    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e8"), "isim" : "Gül", "yas" : 50, "sehir" : "Muş", "Kedi" : 1 }



## $in

Bir listenin içerisinde olan değerleri verir

    db.uyeler.find( { "yas": { $in: [50,21,22]} } )
    
    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e6"), "isim" : "Kerim", "yas" : 22, "sehir" : "İzmir", "Kedi" : 0 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e8"), "isim" : "Gül", "yas" : 50, "sehir" : "Muş", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6ea"), "isim" : "Mustafa", "yas" : 21, "sehir" : "İstanbul", "Kedi" : 0 }


## $lt

Verilen değerden daha küçük olan değerleri verir

    db.uyeler.find( { "yas": { $lt: 20} } )
    
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e9"), "isim" : "İsmail", "yas" : 18, "sehir" : "İstanbul", "Kedi" : 1 }

## $lte

Verilenn değer ve o değerden daha küçük olanlar

    db.uyeler.find( { "yas": { $lte: 20} } )
    
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e9"), "isim" : "İsmail", "yas" : 18, "sehir" : "İstanbul", "Kedi" : 1 }



## $ne

not equal anlamındadadır

    db.uyeler.find( { "yas": { $ne: 20} } )
    
    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 40, "sehir" : "İstanbul" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }


## $nin

İçerisinde olmayan değerleri getir

    db.uyeler.find( { "yas": { $nin: [50,21,22]} } )

    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 40, "sehir" : "İstanbul" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e7"), "isim" : "Davut", "yas" : 35, "sehir" : "Ankara", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e9"), "isim" : "İsmail", "yas" : 18, "sehir" : "İstanbul", "Kedi" : 1 }










# Logical

## $and

Sorgu tümcelerini mantıksal bir AND ile birleştirir, her iki tümcenin koşullarıyla eşleşen tüm belgeleri döndürür.

And'den sonra sıra sıra şartları veriyoruz şeklinde bir yapı vardır.

    db.uyeler.find( { $and: [ { yas: { $gt: 40 } }, { isim: "Ahmet"} ] } )

    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }



## $not

Bu sorgunun tersini verir. Normalde 20'den büyükleri vermesi lazım ama bunu not içerisine aldık böylece tersini veriyor.

    db.uyeler.find( { yas: { $not: { $gt: 20 } } } )

    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e9"), "isim" : "İsmail", "yas" : 18, "sehir" : "İstanbul", "Kedi" : 1 }


## $nor

Sorgu tümcelerini mantıksal bir NOR ile birleştirir, her iki tümceyle eşleşmeyen tüm belgeleri döndürür. Verilen şartlara uymayan verileri getirir

    db.uyeler.find( { $nor: [ { yas: 40 }, { isim: "Ayşe" } ]  })

    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e6"), "isim" : "Kerim", "yas" : 22, "sehir" : "İzmir", "Kedi" : 0 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e7"), "isim" : "Davut", "yas" : 35, "sehir" : "Ankara", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e8"), "isim" : "Gül", "yas" : 50, "sehir" : "Muş", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e9"), "isim" : "İsmail", "yas" : 18, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6ea"), "isim" : "Mustafa", "yas" : 21, "sehir" : "İstanbul", "Kedi" : 0 }



## $or

Verilen şartlardan birine vs uyan verileri getirir

    db.uyeler.find( { $or: [ { yas: 40 }, { isim: "Ayşe" } ]  })

    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 40, "sehir" : "İstanbul" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }




# regex

Regex kullanım imkanı verir.

Genel yapı şu şekilde

    {alan : {"$regex":/pattern/ , $options : "options"}}

Options kısmı için

    i : Büyük küçük harf duyarsızlığı
    m : Her satırın başı ve sonu eşleştirmesi
    s : Yeni satır ve nokta gibi karakterlere izin


Tırnak içerilerine yazabiliriz ya da **//** şeklinde yapı kullanabiliriz.

^a yerine direkt a kullanınca içinde olması yeter diyor ona göre hepsini veriyor. İçinde olan değerleri vermiş oluyor.


    db.uyeler.find({isim:{"$regex":"a", $options:"i"}})

    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e7"), "isim" : "Davut", "yas" : 35, "sehir" : "Ankara", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e9"), "isim" : "İsmail", "yas" : 18, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6ea"), "isim" : "Mustafa", "yas" : 21, "sehir" : "İstanbul", "Kedi" : 0 }

    > db.uyeler.find({isim:{"$regex":"^a", $options:"i"}})
    > 
    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }


Düzgün isim örneği için

    db.uyeler.find({isim:{"$regex":"^Da"}})

        { "_id" : ObjectId("62cefa756592bf0fab88e6e7"), "isim" : "Davut", "yas" : 35, "sehir" : "Ankara", "Kedi" : 1 }

    db.uyeler.find({isim:{"$regex":/^Da/}})

        { "_id" : ObjectId("62cefa756592bf0fab88e6e7"), "isim" : "Davut", "yas" : 35, "sehir" : "Ankara", "Kedi" : 1 }


Örneğin büyük ve küçük harf duyarsızlığını açmamız gerekirse

    db.uyeler.find({isim:{"$regex":/^da/, $options:"i"}})

    { "_id" : ObjectId("62cefa756592bf0fab88e6e7"), "isim" : "Davut", "yas" : 35, "sehir" : "Ankara", "Kedi" : 1 }












# count ve length

Verileri saydırmaya yarar.

    db.uyeler.find().count()

    10

Direkt bunu find yerine kullanıp bu şekilde de arayabiliyoruz

    db.uyeler.count()
    
    10



# limit

gelen veriye limit getirmemizi sağlar.

    db.uyeler.find().limit(2)
    
    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 21, "sehir" : "İstanbul" }









# aggregate

Bir çok belgeyi işler ve bunlara yapılan işlemlerin bir sonucu döndüren ana yapıdır. Bir pipeline yapısı vardır. Bir işlem yapılır, çıktıları alınır sonrasında belirtilen işleme bu çıktılar gönderilir.

## group

Verileri mysql'de vs olduğu gibi gruplamaya yarar. Normalde veriler id değerleine göre gruplanıyor olarak düşünebiliriz. Böylece her veri 1 grubu temsil ediyor ve tekillik sağlanıyor. Bu şekilde gruplama yaparken bu id değerini gruplamak istediğimiz değer ile değiştirerek gruplama yapıyoruz. Burada bir değişken olarak verdiğimiz için **$alan** şeklinde veriyoruz.

    db.uyeler.aggregate({$group:{_id:"$sehir"}})
    
    { "_id" : "İzmir" }
    { "_id" : "İstanbul" }
    { "_id" : "Kanada" }
    { "_id" : "Ankara" }
    { "_id" : "Muş" }


## sum

**Sonrasında count, sum gibi değerler kullanarak pipeline yapısına devam edebilir ve bu şekilde bu gruplardaki eleman sayılarını vs alabiliriz.**

Örnek grup sayısını almak istersek

    db.uyeler.aggregate([{$group:{_id:"$sehir"}},{$count:"total"}])

    { "total" : 5 }

<code>Grupların eleman sayısını almak istersek</code>

Burada sum değeri bir çarpan sayısı. 2 verirsek istanbul 4 yerine 8 oluyor her şeyi 2 ile çarpıyor. Bu yüzden çarpan 1. Eğer count'u group içerisine yazarsak grupladıktan sonra grup içindeki elemanları sayıyor ya da her gruba ait ortalamayı vs veriyor. Bunu eğer pipline mantığında group dışına yazarsak bu sefer gruplar arasındaki değerleri veriyor.

    db.uyeler.aggregate([{$group : {_id:"$sehir", count:{$sum:1}}}])

    { "_id" : "İstanbul", "count" : 4 }
    { "_id" : "Muş", "count" : 1 }
    { "_id" : "Kanada", "count" : 1 }
    { "_id" : "Ankara", "count" : 1 }
    { "_id" : "İzmir", "count" : 3 }


**Eğer genel olarak bütün yaşların toplamını istersek bu durumda gruplama değerini null yaparız böylece grup olmaz ve bize genel toplamı verir.**


    db.uyeler.aggregate([{ $group: { _id : null, yaslarin_toplami : { $sum: "$yas" } } }])

    { "_id" : null, "yaslarin_toplami" : 294 }



## avg

Verilen alanların ortalamasını bulmaya yarar. Örneği gruplama vermeden toplam yaş'ın ortalamasına bakalım.

    db.uyeler.aggregate([{ $group: { _id : null, ortalama : { $avg: "$yas" } } }])

    { "_id" : null, "ortalama" : 29.4 }



## match 

Eşleşme için kullanılan temel fonksiyon yapısıdır. Normaldeki gibi find kullanmadığımız için bu tip yapılarda bu özeliği kullanıyoruz.

    db.uyeler.aggregate([{$match : {"sehir":"İstanbul"}}])
    
    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 21, "sehir" : "İstanbul" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e9"), "isim" : "İsmail", "yas" : 18, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6ea"), "isim" : "Mustafa", "yas" : 21, "sehir" : "İstanbul", "Kedi" : 0 }

Örneğin sadece istanbul'un ortalamasını almaya çalışırsak önce eşleşenleri bulup sonrasında her birini bir grup olarak ele alıp avg uygulayabiliriz.

    db.uyeler.aggregate([{$match : {"sehir":"İstanbul"}}, { $group: { _id : null, ortalama : { $avg: "$yas" } } }])

    { "_id" : null, "ortalama" : 18.75 }

ya da bunu önce gruplayıp sonra bunların ortalamarından match yapıp oradan da alabiliriz

    db.uyeler.aggregate([{$group : {_id : "$sehir", ortalama : {$avg : "$yas"}}}, {$match : {"_id":"İstanbul"}}])



## limit

pipeline içerisinde de limit kullanabiliyoruz.

    db.uyeler.aggregate([{$match : {"sehir":"İstanbul"}}, {$limit:2}])
    
    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 21, "sehir" : "İstanbul" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }













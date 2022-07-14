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





# Evaluation

## $regex

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







# aggregation

## $group

Verileri gruplamaya yarar. Verdiğimiz değere göre verileri grupluyor. Burada **$** işareti unutulmamalı.

    db.uyeler.aggregate([{$group : {_id : "$sehir"}}])


Eğer her veride ne kadar eleman olduğunu öğrenmek istersek sum kullanmamız gerekiyor. Burada sum değerine 1 veriyoruz çünkü gelen değeri 1 ile çarpıyor. Eğer 2 verirsek değeri 2 ile çarpıyor.

    db.uyeler.aggregate([{$group : {_id : "$sehir" ,personel_sayisi : {$sum : 1}}}])
    
    { "_id" : "İstanbul", "personel_sayisi" : 4 }
    { "_id" : "Muş", "personel_sayisi" : 1 }
    { "_id" : "Kanada", "personel_sayisi" : 1 }
    { "_id" : "Ankara", "personel_sayisi" : 1 }
    { "_id" : "İzmir", "personel_sayisi" : 2 }


## sample

Rastgele örnekler alabilmemizi sağlar. Verilen değer kadar örnek alır.

    db.uyeler.aggregate({$sample:{size:3}})

    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 21, "sehir" : "İstanbul" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e7"), "isim" : "Davut", "yas" : 35, "sehir" : "Ankara", "Kedi" : 1 }



## sort

Artan sıralama için 1, azalan sıralama için -1 kullanıyoruz.

    db.uyeler.aggregate({$sort:{"yas":1,"isim":-1}})

    { "_id" : ObjectId("62cefa756592bf0fab88e6e5"), "isim" : "Ayşe", "yas" : 15, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e9"), "isim" : "İsmail", "yas" : 18, "sehir" : "İstanbul", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6ea"), "isim" : "Mustafa", "yas" : 21, "sehir" : "İstanbul", "Kedi" : 0 }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 21, "sehir" : "İstanbul" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e6"), "isim" : "Kerim", "yas" : 22, "sehir" : "İzmir", "Kedi" : 0 }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e7"), "isim" : "Davut", "yas" : 35, "sehir" : "Ankara", "Kedi" : 1 }
    { "_id" : ObjectId("62cefa756592bf0fab88e6e8"), "isim" : "Gül", "yas" : 50, "sehir" : "Muş", "Kedi" : 1 }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e3"), "isim" : "Ahmet", "yas" : 50, "sehir" : "Kanada" }









# limit

Gelecek verileri limitlemeye yarar

    db.uyeler.find().limit(2)

    { "_id" : ObjectId("62cee0756592bf0fab88e6e0"), "isim" : "Ayşe", "yas" : 22, "sehir" : "İzmir" }
    { "_id" : ObjectId("62cee0756592bf0fab88e6e1"), "isim" : "Kerim", "yas" : 21, "sehir" : "İstanbul" }




# sum

Gruplanmış verilere sum yapabiliyoruz fakat normal verileri direkt olarak toplayamıyoruz. Bunun için gruplama verisine null veriyoruz ve her bir değer bir grup haline geliyor ardından bunları toplayarak sonucu buluyoruz. Örneğin verideki yaşların toplamını almak istersek

    db.uyeler.aggregate([{$group: {_id:null, yaslarin_toplami:{$sum:"$yas"}}}])
    
    { "_id" : null, "yaslarin_toplami" : 273 }



# avg

Ortalamayı verir

    db.uyeler.aggregate({$group: {_id:"$sehir", yaslarin_toplami:{$avg:"$yas"}}})
    
    { "_id" : "Muş", "yaslarin_toplami" : 50 }
    { "_id" : "İzmir", "yaslarin_toplami" : 22 }
    { "_id" : "İstanbul", "yaslarin_toplami" : 23.5 }
    { "_id" : "Ankara", "yaslarin_toplami" : 35 }
    { "_id" : "Kanada", "yaslarin_toplami" : 50 }


# first ve last

First: Her grup için ilk belgeden bir değer döndürür. Sipariş, yalnızca belgeler tanımlanmış bir sıradaysa tanımlanır. Örneğin her grubun ilk değerini alıyoruz.

Last ise tam tersini yapar.

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

    db.uyeler.aggregate({$group: {_id:"$sehir", yaslarin_toplami:{$first:"$yas"}}})

        { "_id" : "İstanbul", "yaslarin_toplami" : 40 }
        { "_id" : "Muş", "yaslarin_toplami" : 50 }
        { "_id" : "Kanada", "yaslarin_toplami" : 50 }
        { "_id" : "Ankara", "yaslarin_toplami" : 35 }
        { "_id" : "İzmir", "yaslarin_toplami" : 22 }


# max ve min

Her gruptaki max ve min değerleri verir.

    db.uyeler.aggregate({$group: {_id:"$sehir", yaslarin_toplami:{$max:"$yas"}}})

    { "_id" : "İstanbul", "yaslarin_toplami" : 40 }
    { "_id" : "Muş", "yaslarin_toplami" : 50 }
    { "_id" : "Kanada", "yaslarin_toplami" : 50 }
    { "_id" : "Ankara", "yaslarin_toplami" : 35 }
    { "_id" : "İzmir", "yaslarin_toplami" : 22 }




# push

Grupların içerik değerlerini bir liste içerisinde verir.

    db.uyeler.aggregate({$group: {_id:"$sehir", yaslarin_toplami:{$push:"$yas"}}})

    { "_id" : "İzmir", "yaslarin_toplami" : [ 22, 22 ] }
    { "_id" : "İstanbul", "yaslarin_toplami" : [ 40, 15, 18, 21 ] }
    { "_id" : "Kanada", "yaslarin_toplami" : [ 50 ] }
    { "_id" : "Ankara", "yaslarin_toplami" : [ 35 ] }
    { "_id" : "Muş", "yaslarin_toplami" : [ 50 ] }


# addToSet

Her gruptaki her bir bağımsız farklı değeri verir. İstanbul'da 2 tane 21 yaşında olmasına rağmen bize bir tane gösteriyor.

    db.uyeler.aggregate({$group: {_id:"$sehir", yaslarin_toplami:{$addToSet:"$yas"}}})

    { "_id" : "İstanbul", "yaslarin_toplami" : [ 18, 21, 15 ] }
    { "_id" : "Muş", "yaslarin_toplami" : [ 50 ] }
    { "_id" : "Kanada", "yaslarin_toplami" : [ 50 ] }
    { "_id" : "Ankara", "yaslarin_toplami" : [ 35 ] }
    { "_id" : "İzmir", "yaslarin_toplami" : [ 22 ] }


# stdDevPop

Popülasyon standart sapmalarını verir.

    db.uyeler.aggregate({$group: {_id:"$sehir", yaslarin_toplami:{$stdDevPop:"$yas"}}})

    { "_id" : "İstanbul", "yaslarin_toplami" : 2.48746859276655 }
    { "_id" : "Muş", "yaslarin_toplami" : 0 }
    { "_id" : "Kanada", "yaslarin_toplami" : 0 }
    { "_id" : "Ankara", "yaslarin_toplami" : 0 }
    { "_id" : "İzmir", "yaslarin_toplami" : 0 }


# stdDevSamp

Örnek standart sapmalarını verir

    db.uyeler.aggregate({$group: {_id:"$sehir", yaslarin_toplami:{$stdDevSamp:"$yas"}}})
    
    { "_id" : "İstanbul", "yaslarin_toplami" : 2.8722813232690143 }
    { "_id" : "Muş", "yaslarin_toplami" : null }
    { "_id" : "Kanada", "yaslarin_toplami" : null }
    { "_id" : "Ankara", "yaslarin_toplami" : null }
    { "_id" : "İzmir", "yaslarin_toplami" : 0 }




















































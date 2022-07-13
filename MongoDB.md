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















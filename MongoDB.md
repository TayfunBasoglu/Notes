# Database


## Listelemek

    show dbs
    
    admin     0.000GB
    config    0.000GB
    deneme    0.000GB
    local     0.000GB
    ornekler  0.000GB

## Oluşturma

Diğerlerinden farklı olarak içeriisne veri girilmediği zaman teknik olarak bir veri tabanı oluşturulmuş olmuyor.

    use deneme;
    db.deneme.insert({isim:"ahmet"})
    db.deneme.find()

    { "_id" : ObjectId("62cedac86592bf0fab88e6de"), "isim" : "ahmet" }


## Silme

Bir database içerisine use ile girdikten sonra **dropDatabase** kullanılıyor.

        db.dropDatabase()

        admin     0.000GB
        config    0.000GB
        local     0.000GB
        ornekler  0.000GB



































































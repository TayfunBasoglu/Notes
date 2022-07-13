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














































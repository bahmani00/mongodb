# mongodb

docker compose up

docker compose down


docker exec -it 48217290a098 bash  <- (mongodb image)


login into mongo db:

bash-5.0# mongosh mongodb://127.0.0.1:27017 -u rootuser -p rootpass

bash-5.0# show dbs

    admin       100.00 KiB
    config       92.00 KiB
    local        72.00 KiB
    
    
bash-5.0# use amigoscode  <- if doesnt exist it creates it

bash-5.0# db.createCollection("person")

{ ok: 1 }


bash-5.0# show collections

person

--------------
db.createUser({
   user: "dan",
   pwd: "1234",
   roles: ["readWrite", "dbAdmin"]
});

Successfully added user { user: "dan", pwd: "1234", roles: ["readWrite", "dbAdmin"] }

--------------
db.person.insert({first_name: "John", last_name: "Doe"})

to add Gender to John:

db.person.update({first_name: "John"}, {last_name: "Doe"}, {first_name: "John", last_name: "Doe", gender: "male"})

or simpler:

db.person.update({first_name: "John"}, {$set: {gender: "male"}})

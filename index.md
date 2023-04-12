db.emp.insert({emp_id:1001,name:"rahul",lastname:"patel",email:"rahulh@google.com",phone:9874561237,Job_id:'E3',sal:80000,manager_id:'102'})
db.emp.insert({emp_id:1002,name:"ankit",lastname:"bajpai",email:"ankit@google.com",phone:9852617775,Job_id:'E4',sal:70000,manager_id:'103'})
db.emp.insert({emp_id:1003,name:"swati",lastname:"singla",email:"swati@google.com",phone:9745261738,Job_id:'E4',sal:60000,manager_id:'104',arr:['a','b','c','d']})
db.emp.insert({emp_id:1004,name:"yash",lastname:"sharma",email:"yash@google.com",phone:98745614455,Job_id:'E3',sal:77000,manager_id:'102'})
db.emp.insert({emp_id:1005,name:"alaykhyaa",lastname:"bajpai",email:"alaykhyaa@google.com",phone:98526173999,Job_id:'E4',sal:89000,manager_id:'103'})

db.emp.getIndexes()

db.emp.createIndexes({"job_id":1})

db.emp.dropIndexes({"job_id":1})


db.article.insert([
     {"text":"ind11ia with cricket","tags":["ind12ia","cricket"]},
      {"text":"economy of india","tags":["economy","india"]},
 {"text":"nature and beatuy of himalays","tags":["himalays","nature"]}, {"text":"beauty of india","tags":["beauty","ind"]}
  ])

  db.article.createIndex({text:"text"})

  db.article.find({$text:{$search:'india'}})
  db.article.find({tag:{$regex:'ind'}}).pretty()

  db.article.find({tag:{$regex:'h'}}).pretty()


  db.emp.reIndex({"phone":1})

  ////ttl
  db.emp.createIndex({"phone":1},{expireAfterSecounds:3600})

  db.emp.createIndex({'phone':1},{background:true})

db.places.insert({"name":"mobile","type":"elec","location":[40.232,-74.343]})
db.places.insert({"name":"tv","type":"elec","location":[50.232,-84.343]})
db.places.insert({"name":"cloths","type":"cloths","location":[60.232,-94.343]})

db.place.find({location:{$near:[40, -60]}})

db.place.find({location:{$near:[70, -64]}}).limit(2).pretty()


db.shops.reIndex({location:"2dsphere"})
db.shops.find({ location:{$near:{$geometry:{type:"Point",coordinates:[100,56]},
 $maxDistance:9000000 }} }).pretty()
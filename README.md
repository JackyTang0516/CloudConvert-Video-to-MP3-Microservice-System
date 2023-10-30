# mp3_converter

How to run:



1. To start RabbitMQ:
minikube start
minikube tunnel

2. create a jwt token:(the token does not contains %)
curl -X POST http://mp3converter.com/login -u email:password(in the data base)

3. refresh the gateway
cd gateway 
kubectl delete  -f ./manifests
kubectl apply -f ./manifests
kubectl scale deployment --replicas=1 converter servicename

5. send a email to notice the mp3 file was genetated 
curl -X POST -F 'file=@./test.mkv' -H 'Authorization: Bearer jwt_token’
http://mp3converter.com/upload

7. see email for the mp3 id:(pay attention to ’ character)
curl --output mp3_download.mp3 -X GET -H 'Authorization: Bearer jwttoken' "http://mp3converter.com/download?fid=file_id(get from email)"


To set environment path of RabbitMQ Manager:
On mac: sudo vim /etc/hosts
127.0.0.1 mp3converter.com
127.0.0.1 rabbitmq-manager.com





docker build ./
username
docker tag image username/servicename:latest
docker push username/servicename:latest
kubectl delete  -f ./manifests
kubectl apply -f ./manifests

kubectl logs -f name&id in k9s
kubectl scale deployment --replicas=1 converter servicename

To create a jwt token:(the token does not contains %)
curl -X POST http://mp3converter.com/login -u email:password(in the data base)

To start upload the video:
curl -X POST -F 'file=@./videoname' -H 'Authorization: Bearer jwt token'
http://mp3converter.com/upload

You should reset the gateway service in k9s since the host of rabbitmq will not connect it well


Find mp3id in mongodb:
mongosh
show databases;
use mp3s
show collections
db.fs.files.find()
To find id of converted mp3:
db.fs.files.find({"_id": ObjectId("651bb6f2d98f57da8c80c8c4")})
To get mp3 file from mongodb to the local:
converter % mongofiles --db=mp3s get_id --local=test.mp3 '{"$oid":"651bb6f2d98f57da8c80c8c4"}'

Start mysql database:
sudo /usr/local/mysql/support-files/mysql.server start 
mysql -uroot -p
show databases;
use auth
select * from user;
UPDATE user SET email = 'email' WHERE id = 1;



How to download form id:
curl --output mp3_download.mp3 -X GET -H 'Authorization: Bearer jwt_token' 
"http://mp3converter.com/download?fid=651bb6f2d98f57da8c80c8c4"

Use google 2-step authentication                                            



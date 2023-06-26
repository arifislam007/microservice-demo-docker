# microservice-demo-docker
# Google Microservice Demo run on docker or docker compose
First download the repository from git 
git clone https://github.com/arifislam007/microservices-demo.git

Then build all images on docker host. in the repo you will get all dockerfile in src directory. Go there an build all images as per following list:
- adservice
- cartservice
- checkoutservice
- currencyservice
- emailservice
- frontend
- loadgenerator
- paymentservice
- productcatalogservice
- recommendationservice
- shippingservice

# Build all images </br>
docker build -t front:v1 . </br>
docker build -t advise:v1 . </br>
docker build -t cart:v1 . </br>
docker build -t checkout:v1 . </br>
docker build -t curr:v1 . </br>
docker build -t email:v1 . </br>
docker build -t load:v1 . </br>
docker build -t payment:v1 . </br>
docker build -t productcata:v1 . </br>
docker build -t recommand:v1 .
docker build -t shipp:v1 .


Now Create environment file in you project direcoty for up all the servcie and dependency. Also all container releted on the project will run on a different network in docker. In my case I run on demo network. 
create an env file for running all container service with the following content in the file:

PRODUCT_CATALOG_SERVICE_ADDR=productcatalogservice:3550

CURRENCY_SERVICE_ADDR=currencyservice:7000

SHIPPING_SERVICE_ADDR=shippingservice:50051

PAYMENT_SERVICE_ADDR=paymentservice:50051

EMAIL_SERVICE_ADDR=emailservice:5000

CART_SERVICE_ADDR=cartservice:7070

RECOMMENDATION_SERVICE_ADDR=recommendationservice:8080

SHIPPING_SERVICE_ADDR=shippingservice:50051

CHECKOUT_SERVICE_ADDR=checkoutservice:5050

AD_SERVICE_ADDR=adservice:9555

# Now run images with the enviornmet file.

docker run -itd --network demo --env-file env --name adservice -p 9555:9555 advise:v1
docker run -itd --network demo --env-file env --name cartservice -p 7070:7070 cart:v1
docker run -itd --network demo --env-file env --name checkoutservice -p 5050:5050 checkout:v1
docker run -itd --network demo --env-file env --name currencyservice -p 7000:7000 curr:v1
docker run -itd --network demo --env-file env --name emailservice -p 5000:8080 email:v1
docker run -itd --network demo --env-file env --name paymentservice -p 50051 payment:v1
docker run -itd --name frontend -p 80:8080 --network demo --env-file env frontend:v1
docker run -itd --network demo --env-file env --name recommendationservice -p 8080:8080 recommand:v1
docker run -itd --network demo --env-file env --name shippingservice shipp:v1


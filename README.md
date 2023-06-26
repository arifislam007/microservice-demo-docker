# microservice-demo-docker
#Google Microservice Demo run on docker or docker compose
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

Now Create environment file in you project direcoty for up all the servcie and dependency. Also all container releted on the project will run on a different network in docker. In my case I run on demo network. 
create an env file for frontend service with the following content in the file:

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





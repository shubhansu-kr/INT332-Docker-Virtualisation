kubectl delete deployments auth-depl              
kubectl delete deployments auth-mongo-depl        
kubectl delete deployments client-depl            
kubectl delete deployments expiration-depl        
kubectl delete deployments expiration-redis-depl  
kubectl delete deployments nats-depl              
kubectl delete deployments orders-depl            
kubectl delete deployments orders-mongo-depl      
kubectl delete deployments payments-depl          
kubectl delete deployments payments-mongo-depl    
kubectl delete deployments tickets-depl           
kubectl delete deployments tickets-mongo-depl 

kubectl delete services auth-srv
kubectl delete services auth-mongo-srv
kubectl delete services client-srv
kubectl delete services expiration-srv
kubectl delete services expiration-redis-srv
kubectl delete services nats-srv
kubectl delete services orders-srv
kubectl delete services orders-mongo-srv
kubectl delete services payments-srv
kubectl delete services payments-mongo-srv
kubectl delete services tickets-srv
kubectl delete services tickets-mongo-srv

docker build -t shubhansukr/auth .
docker push shubhansukr/auth

docker build -t shubhansukr/<serviceName> .
docker push shubhansukr/<serviceName>

kubectl apply -f .
kubectl get deployments
kubectl get services
kubectl get pods 

kubectl delete deployments <depName>
kubectl delete services <srvName>


Generating tags...
 - shubhansukr/auth -> shubhansukr/auth:latest
 - shubhansukr/ticketing-client -> shubhansukr/ticketing-client:latest
 - shubhansukr/tickets -> shubhansukr/tickets:latest
 - shubhansukr/orders -> shubhansukr/orders:latest
 - shubhansukr/expiration -> shubhansukr/expiration:latest
 - shubhansukr/payments -> shubhansukr/payments:latest
Some taggers failed. Rerun with -vdebug for errors.
Checking cache...
 - shubhansukr/auth: Found Locally
 - shubhansukr/ticketing-client: Found. Tagging
 - shubhansukr/tickets: Found Locally
 - shubhansukr/orders: Found Locally
 - shubhansukr/expiration: Found Locally
 - shubhansukr/payments: Found Locally
Tags used in deployment:
 - shubhansukr/auth -> shubhansukr/auth:47f7849c3035ecd2dcab50b73c438218ad9508593b3011f2e5e7bfd89e7810f9
 - shubhansukr/ticketing-client -> shubhansukr/ticketing-client:a6b86b292d941347cea04b3ae4ab6e9b78a7d40fe14ec5e1aec3381eefb6ae12
 - shubhansukr/tickets -> shubhansukr/tickets:22e2159094809b134a85f8119256f98db91231e8eff71d8456c2f0233a90b208
 - shubhansukr/orders -> shubhansukr/orders:7182242d35c3805ad04cafec05df6b847422e5f6c30f1b250340965b310e66ba
 - shubhansukr/expiration -> shubhansukr/expiration:78acdb5f649282546f761797a24d4463466506d49c412bfbc6128b9922f7874a
 - shubhansukr/payments -> shubhansukr/payments:e564b5f4e4da34220ef6029271f9056c113beecc827ca530799ae8e959c2ef23
Starting deploy...
 - deployment.apps/auth-depl configured
 - service/auth-srv configured
 - deployment.apps/auth-mongo-depl configured
 - service/auth-mongo-srv configured
 - deployment.apps/client-depl configured
 - service/client-srv configured
 - deployment.apps/expiration-depl configured
 - deployment.apps/expiration-redis-depl configured
 - service/expiration-redis-srv configured
 - deployment.apps/nats-depl configured
 - service/nats-srv configured
 - deployment.apps/orders-depl configured
 - service/orders-srv configured
 - deployment.apps/orders-mongo-depl configured
 - service/orders-mongo-srv configured
 - deployment.apps/payments-depl configured
 - service/payments-srv configured
 - deployment.apps/payments-mongo-depl configured
 - service/payments-mongo-srv configured
 - deployment.apps/tickets-depl configured
 - service/tickets-srv configured
 - deployment.apps/tickets-mongo-depl configured
 - service/tickets-mongo-srv configured
 - ingress.networking.k8s.io/ingress-service unchanged
Waiting for deployments to stabilize...
 - deployment/nats-depl is ready. [11/12 deployment(s) still pending]
 - deployment/auth-mongo-depl is ready. [10/12 deployment(s) still pending]
 - deployment/auth-depl: creating container auth
    - pod/auth-depl-7cf66b477d-qcthm: creating container auth
 - deployment/client-depl: creating container client
    - pod/client-depl-7594b9bf45-z45st: creating container client
 - deployment/expiration-depl: creating container expiration
    - pod/expiration-depl-58fb6db798-5c4d8: creating container expiration
 - deployment/expiration-redis-depl: creating container expiration-redis
    - pod/expiration-redis-depl-56d8699bd5-t999v: creating container expiration-redis
 - deployment/orders-depl: creating container orders
    - pod/orders-depl-695798f57b-gmh2j: creating container orders
 - deployment/orders-mongo-depl: creating container orders-mongo
    - pod/orders-mongo-depl-55c9d47c56-7gqsm: creating container orders-mongo
 - deployment/payments-depl: creating container payments
    - pod/payments-depl-6cdcbdb7c8-smnkt: creating container payments
 - deployment/payments-mongo-depl: creating container payments-mongo
    - pod/payments-mongo-depl-dfc89c45b-wrbnn: creating container payments-mongo
 - deployment/tickets-depl: creating container tickets
    - pod/tickets-depl-5764c965b8-2zmmf: creating container tickets
 - deployment/tickets-mongo-depl: creating container tickets-mongo
    - pod/tickets-mongo-depl-999cb689b-bfjpr: creating container tickets-mongo
I0501 01:52:06.612125   18468 request.go:697] Waited for 1.0642349s due to client-side throttling, not priority and fairness, request: GET:https://kubernetes.docker.internal:6443/apis/apps/v1/namespaces/default/replicasets?labelSelector=app%3Dexpiration-redis
 - deployment/auth-depl: container auth is waiting to start: shubhansukr/auth:47f7849c3035ecd2dcab50b73c438218ad9508593b3011f2e5e7bfd89e7810f9 can't be pulled
    - pod/auth-depl-7cf66b477d-qcthm: container auth is waiting to start: shubhansukr/auth:47f7849c3035ecd2dcab50b73c438218ad9508593b3011f2e5e7bfd89e7810f9 can't be pulled
 - deployment/auth-depl failed. Error: container auth is waiting to start: shubhansukr/auth:47f7849c3035ecd2dcab50b73c438218ad9508593b3011f2e5e7bfd89e7810f9 can't be pulled.
Cleaning up...
 - deployment.apps "auth-depl" deleted
 - service "auth-srv" deleted
 - deployment.apps "auth-mongo-depl" deleted
 - service "auth-mongo-srv" deleted
 - deployment.apps "client-depl" deleted
 - service "client-srv" deleted
 - deployment.apps "expiration-depl" deleted
 - deployment.apps "expiration-redis-depl" deleted
 - service "expiration-redis-srv" deleted
 - deployment.apps "nats-depl" deleted
 - service "nats-srv" deleted
 - deployment.apps "orders-depl" deleted
 - service "orders-srv" deleted
 - deployment.apps "orders-mongo-depl" deleted
 - service "orders-mongo-srv" deleted
 - deployment.apps "payments-depl" deleted
 - service "payments-srv" deleted
 - deployment.apps "payments-mongo-depl" deleted
 - service "payments-mongo-srv" deleted
 - deployment.apps "tickets-depl" deleted
 - service "tickets-srv" deleted
 - deployment.apps "tickets-mongo-depl" deleted
 - service "tickets-mongo-srv" deleted
 - ingress.networking.k8s.io "ingress-service" deleted
1/12 deployment(s) failed


  Id CommandLine                                                                                                                              
  -- -----------                                                                                                                              
   1 try { . "c:\Users\12345\AppData\Local\Programs\Microsoft VS Code\resources\app\out\vs\workbench\contrib\terminal\browser\media\shellIn...
   2 cd .\infra\ 
   3 cd .\k8s\ 
   4 clear 
   5 cd .. 
   6 cd .. 
   7 cd .\auth\ 
   8 ls 
   9 docker build -t shubhansukr/auth 
  10 docker build -t shubhansukr/auth . 
  11 docker images 
  12 cd .. 
  13 cd .\client\ 
  14 docker build -t shubhansukr/client . 
  15 cd .. 
  16 cd .\common\ 
  17 ls 
  18 cd .. 
  19 cd .\expiration\ 
  20 l 
  21 ls 
  22 docker build -t shubhansukr/expiration . 
  23 cd ..\nats-test\ 
  24 ls 
  25 cd ..\orders\ 
  26 ls 
  27 docker build -t shubhansukr/orders . 
  28 cd ..\payments\ 
  29 ls 
  30 docker build -t shubhansukr/payments . 
  31 cd .. 
  32 cd .\tickets\ 
  33 docker build -t shubhansukr/tickets . 
  34 clear 
  35 cd .. 
  36 docker images 
  37 docker push shubhansukr/auth 
  38 docker push shubhansukr/client 
  39 docker push shubhansukr/expiration 
  40 docker push shubhansukr/orders 
  41 docker push shubhansukr/payments 
  42 docker push shubhansukr/tickets 
  43 clear 
  44 cd .\infra\ 
  45 cd .\k8s\ 
  46 kubectl apply -f . 
  47 kubectl get deployments 
  48 kubectl get services 
  49 kubectl get deployments 
  50 kubectl get deployments 
  51 kubectl get deployments 
  52 clear 
  53 cd .. 
  54 cd .. 
  55 skaffold dev 


Generating tags...
 - shubhansukr/auth -> shubhansukr/auth:latest
 - shubhansukr/ticketing-client -> shubhansukr/ticketing-client:latest
 - shubhansukr/tickets -> shubhansukr/tickets:latest
 - shubhansukr/orders -> shubhansukr/orders:latest
 - shubhansukr/expiration -> shubhansukr/expiration:latest
 - shubhansukr/payments -> shubhansukr/payments:latest
Some taggers failed. Rerun with -vdebug for errors.
Checking cache...
 - shubhansukr/auth: Found Locally
 - shubhansukr/ticketing-client: Found Locally
 - shubhansukr/tickets: Found Locally
 - shubhansukr/orders: Found Locally
 - shubhansukr/expiration: Found Locally
 - shubhansukr/payments: Found Locally
Tags used in deployment:
 - shubhansukr/auth -> shubhansukr/auth:47f7849c3035ecd2dcab50b73c438218ad9508593b3011f2e5e7bfd89e7810f9
 - shubhansukr/ticketing-client -> shubhansukr/ticketing-client:a6b86b292d941347cea04b3ae4ab6e9b78a7d40fe14ec5e1aec3381eefb6ae12
 - shubhansukr/tickets -> shubhansukr/tickets:22e2159094809b134a85f8119256f98db91231e8eff71d8456c2f0233a90b208
 - shubhansukr/orders -> shubhansukr/orders:7182242d35c3805ad04cafec05df6b847422e5f6c30f1b250340965b310e66ba
 - shubhansukr/expiration -> shubhansukr/expiration:78acdb5f649282546f761797a24d4463466506d49c412bfbc6128b9922f7874a
 - shubhansukr/payments -> shubhansukr/payments:e564b5f4e4da34220ef6029271f9056c113beecc827ca530799ae8e959c2ef23
Starting deploy...
 - deployment.apps/auth-depl created
 - service/auth-srv created
 - deployment.apps/auth-mongo-depl created
 - service/auth-mongo-srv created
 - deployment.apps/client-depl created
 - service/client-srv created
 - deployment.apps/expiration-depl created
 - deployment.apps/expiration-redis-depl created
 - service/expiration-redis-srv created
 - deployment.apps/nats-depl created
 - service/nats-srv created
 - deployment.apps/orders-depl created
 - service/orders-srv created
 - deployment.apps/orders-mongo-depl created
 - service/orders-mongo-srv created
 - deployment.apps/payments-depl created
 - service/payments-srv created
 - deployment.apps/payments-mongo-depl created
 - service/payments-mongo-srv created
 - deployment.apps/tickets-depl created
 - service/tickets-srv created
 - deployment.apps/tickets-mongo-depl created
 - service/tickets-mongo-srv created
 - Warning: annotation "kubernetes.io/ingress.class" is deprecated, please use 'spec.ingressClassName' instead
 - ingress.networking.k8s.io/ingress-service created
Waiting for deployments to stabilize...
 - deployment/client-depl is ready. [11/12 deployment(s) still pending]
 - deployment/nats-depl is ready. [10/12 deployment(s) still pending]
 - deployment/auth-depl is ready. [9/12 deployment(s) still pending]
 - deployment/orders-depl is ready. [8/12 deployment(s) still pending]
 - deployment/expiration-depl is ready. [7/12 deployment(s) still pending]
 - deployment/payments-depl is ready. [6/12 deployment(s) still pending]
 - deployment/tickets-depl is ready. [5/12 deployment(s) still pending]
 - deployment/auth-mongo-depl is ready. [4/12 deployment(s) still pending]
 - deployment/expiration-redis-depl: creating container expiration-redis
    - pod/expiration-redis-depl-8544f4d96b-ggh8l: creating container expiration-redis
 - deployment/orders-mongo-depl: creating container orders-mongo
    - pod/orders-mongo-depl-75f75b8ff5-gwtwp: creating container orders-mongo
 - deployment/payments-mongo-depl: creating container payments-mongo
    - pod/payments-mongo-depl-644d78bd87-zgplz: creating container payments-mongo
 - deployment/tickets-mongo-depl: creating container tickets-mongo
    - pod/tickets-mongo-depl-754f9b44f-r6bl5: creating container tickets-mongo
 - deployment/expiration-redis-depl is ready. [3/12 deployment(s) still pending]
 - deployment/orders-mongo-depl is ready. [2/12 deployment(s) still pending]
 - deployment/payments-mongo-depl is ready. [1/12 deployment(s) still pending]
 - deployment/tickets-mongo-depl is ready.
Deployments stabilized in 17.247 seconds
Listing files to watch...
 - shubhansukr/auth
 - shubhansukr/ticketing-client
 - shubhansukr/tickets
 - shubhansukr/orders
 - shubhansukr/expiration
 - shubhansukr/payments
Press Ctrl+C to exit
Watching for changes...
[expiration] 
[payments]
[orders]
[expiration] > expiration@1.0.0 start
[payments] > payments@1.0.0 start
[tickets]
[orders] > orders@1.0.0 start
[client]
[auth]
[expiration] > ts-node-dev --poll src/index.ts
[payments] > ts-node-dev --poll src/index.ts
[tickets] > tickets@1.0.0 start
[orders] > ts-node-dev --poll src/index.ts
[client] > client@1.0.0 dev
[auth] > auth@1.0.0 start
[expiration]
[payments]
[tickets] > ts-node-dev --poll src/index.ts
[orders]
[client] > next
[auth] > ts-node-dev --poll src/index.ts
[expiration] [INFO] 20:28:47 ts-node-dev ver. 2.0.0 (using ts-node ver. 10.9.2, typescript ver. 5.4.5)
[payments] [INFO] 20:28:47 ts-node-dev ver. 2.0.0 (using ts-node ver. 10.9.2, typescript ver. 5.4.5)
[tickets]
[tickets] [INFO] 20:28:47 ts-node-dev ver. 2.0.0 (using ts-node ver. 10.9.2, typescript ver. 5.4.5)
[client]
[auth]
[expiration] Connected to NATS
[payments] (node:25) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
[orders] [INFO] 20:28:47 ts-node-dev ver. 2.0.0 (using ts-node ver. 10.9.2, typescript ver. 5.4.5)
[orders] (node:25) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
[orders] (Use `node --trace-deprecation ...` to show where the warning was created)
[auth] [INFO] 20:28:47 ts-node-dev ver. 2.0.0 (using ts-node ver. 10.9.2, typescript ver. 5.4.5)
[payments] (Use `node --trace-deprecation ...` to show where the warning was created)
[tickets] (node:26) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
[client] Attention: Next.js now collects completely anonymous telemetry regarding usage.
[client] This information is used to shape Next.js' roadmap and prioritize features.
[auth] (node:25) [DEP0040] DeprecationWarning: The `punycode` module is deprecated. Please use a userland alternative instead.
[payments] Connected to NATS
[tickets] (Use `node --trace-deprecation ...` to show where the warning was created)
[orders] Connected to NATS
[client] You can learn more, including how to opt-out if you'd not like to participate in this anonymous program, by visiting the following URL:
[auth] (Use `node --trace-deprecation ...` to show where the warning was created)
[auth] Connected to MongoDb
[tickets] Connected to NATS
[orders] Connected to MongoDb
[client] https://nextjs.org/telemetry
[payments] Connected to MongoDb
[auth] Listening on port 3000!!!!!!!!
[orders] Listening on port 3000!!!!!!!!
[client]
[payments] Listening on port 3000!!!!!!!!
[client]   ▲ Next.js 13.5.6
[client]   - Local:        http://localhost:3000
[client]
[client]  ✓ Ready in 6.4s
[tickets] Connected to MongoDb
[tickets] Listening on port 3000!!!!!!!!



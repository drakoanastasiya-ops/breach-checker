{"status":"ok"}
172.20.0.1 - - [12/Nov/2026 08:49:39] "GET /health HTTP/1.1" 200 -







1.
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker run --rm --network breach-net healthcheck-probe
{"status":"ok"}
backend: OK

2.
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker run --rm healthcheck-probe
curl: (6) Could not resolve host: backend (Domain name not found)
backend: UNREACHABLE

3.
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker stop backend
backend
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker run --rm --network breach-net healthcheck-probe
curl: (6) Could not resolve host: backend (Domain name not found)
backend: UNREACHABLE





PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker exec backend sh -c "echo notatka > /tmp/notatka.txt"
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker restart backend
backend
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker exec backend cat /tmp/notatka.txt
notatka
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker rm -f backend
backend
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker run -d --name backend --network breach-net -p 5000:5000 -v ./data/leaked-sha1.txt:/app/data/leaked-sha1.txt:ro breach-checker-backend:v1
e4aa56e69c6f7a68ed6cde7a183cf3ac60afe304ec1959426b6c71ddcb9947d8
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker exec backend cat /tmp/notatka.txt
cat: /tmp/notatka.txt: No such file or directory
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 








PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker run --rm -v breach-dane:/dane alpine sh -c "date >> /dane/historia.txt; cat /dane/historia.txt"
Wed Nov 11 23:22:36 UTC 2026
Wed Nov 11 23:23:09 UTC 2026
Wed Nov 11 23:23:24 UTC 2026
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker volume ls
DRIVER    VOLUME NAME
local     1e1032fc39c0595ff4c7d4ba78e2b1d8bb04b91954a2b161836fd0e06f9031a7
local     4a183fd84e135a19c4b15a682a3a8ca5a484c2f814a702847c782279e5910117
local     614899a8547ba72f9eb7e6b25496500c58e8c9c17b846ef3fc9adc641f4a55c0
local     breach-dane
local     budet_domowy_postgres_data
local     c335dd56672d24f93e639d58347fd52f68005d6f163df89cd9ca54f99c01b935
local     d1eec0e1e9545a6d5fe0f5111d7bef58f95cc301223d6aeb1d4a54dcacc66691
local     fa302077b175ccb42c16710a3bfbaad64c2e239bd6111970a0dc8b1c49138f80
local     index.html
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 


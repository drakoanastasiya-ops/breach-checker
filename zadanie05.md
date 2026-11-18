PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose up -d --scale backend=3
[+] up 5/5
 ✔ Container metody_wirt_lab-frontend-1 Running                                                    0.0s
 ✔ Container metody_wirt_lab-backend-1  Healthy                                                    6.5s
 ✔ Container metody_wirt_lab-db-1       Healthy                                                    0.6s
 ✔ Container metody_wirt_lab-backend-3  Healthy                                                    6.5s
 ✔ Container metody_wirt_lab-backend-2  Healthy                                                    6.5s
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose ps
NAME                         IMAGE                      COMMAND                  SERVICE    CREATED              STATUS                        PORTS
metody_wirt_lab-backend-1    metody_wirt_lab-backend    "python app.py"          backend    About a minute ago   Up About a minute (healthy)   5000/tcp
metody_wirt_lab-backend-2    metody_wirt_lab-backend    "python app.py"          backend    9 seconds ago        Up 8 seconds (healthy)        5000/tcp
metody_wirt_lab-backend-3    metody_wirt_lab-backend    "python app.py"          backend    9 seconds ago        Up 8 seconds (healthy)        5000/tcp
metody_wirt_lab-db-1         postgres:16-alpine         "docker-entrypoint.s…"   db         About a minute ago   Up About a minute (healthy)   5432/tcp
metody_wirt_lab-frontend-1   metody_wirt_lab-frontend   "/docker-entrypoint.…"   frontend   About a minute ago   Up About a minute             0.0.0.0:8080->80/tcp, [::]:8080->80/tcp
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose exec frontend nslookup backend
Server:         127.0.0.11
Address:        127.0.0.11:53

Non-authoritative answer:

Non-authoritative answer:
Name:   backend
Address: 172.19.0.5
Name:   backend
Address: 172.19.0.6
Name:   backend
Address: 172.19.0.3

PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> # Windows PowerShell
>> 1..20 | ForEach-Object { '{"hash":"bc45408273d7e1914b741c3407b0b559764f7876"}' | curl.exe -s -X POST http://localhost:8080/api/check -H "Content-Type: application/json" -d '@-' }
>> 
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
{"found":false}
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose logs backend
backend-3  | W bazie jest 89 hashy
backend-1  | W bazie jest 89 hashy
backend-1  |  * Serving Flask app 'app'
backend-1  |  * Debug mode: off
backend-3  |  * Serving Flask app 'app'
backend-3  |  * Debug mode: off
backend-3  | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
backend-1  | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
backend-1  |  * Running on all addresses (0.0.0.0)
backend-1  |  * Running on http://127.0.0.1:5000
backend-1  |  * Running on http://172.19.0.3:5000
backend-1  | Press CTRL+C to quit
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:26:45] "GET /health HTTP/1.1" 200 -
backend-3  |  * Running on all addresses (0.0.0.0)
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:26:50] "GET /health HTTP/1.1" 200 -
backend-3  |  * Running on http://127.0.0.1:5000
backend-1  | check: hash=bc454...
backend-3  |  * Running on http://172.19.0.5:5000
backend-3  | Press CTRL+C to quit
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:00] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:05] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:10] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:15] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:20] "GET /health HTTP/1.1" 200 -
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:26:51] "POST /check HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:26:55] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:01] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:26] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:31] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:36] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:06] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:11] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:16] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:21] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:26] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:31] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:41] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:46] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:36] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:51] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:41] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:46] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:51] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:56] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:01] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:07] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:12] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:17] "GET /health HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-2  | W bazie jest 89 hashy
backend-2  |  * Serving Flask app 'app'
backend-2  |  * Debug mode: off
backend-2  | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
backend-2  |  * Running on all addresses (0.0.0.0)
backend-2  |  * Running on http://127.0.0.1:5000
backend-2  |  * Running on http://172.19.0.6:5000
backend-2  | Press CTRL+C to quit
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:00] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:05] "GET /health HTTP/1.1" 200 -
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:10] "GET /health HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:22] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:27] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:32] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:37] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:42] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:47] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:52] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:16] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:21] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:26] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:31] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:36] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:41] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:46] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:51] "GET /health HTTP/1.1" 200 -
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose restart frontend
[+] restart 0/1
 - Container metody_wirt_lab-frontend-1 Restarting                                                 0.5s
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose logs backend
backend-3  | W bazie jest 89 hashy
backend-3  |  * Serving Flask app 'app'
backend-3  |  * Debug mode: off
backend-1  | W bazie jest 89 hashy
backend-3  | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
backend-3  |  * Running on all addresses (0.0.0.0)
backend-3  |  * Running on http://127.0.0.1:5000
backend-3  |  * Running on http://172.19.0.5:5000
backend-3  | Press CTRL+C to quit
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:00] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:05] "GET /health HTTP/1.1" 200 -
backend-1  |  * Serving Flask app 'app'
backend-1  |  * Debug mode: off
backend-1  | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
backend-1  |  * Running on all addresses (0.0.0.0)
backend-1  |  * Running on http://127.0.0.1:5000
backend-1  |  * Running on http://172.19.0.3:5000
backend-1  | Press CTRL+C to quit
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:26:45] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:26:50] "GET /health HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:26:51] "POST /check HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:26:55] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:01] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:06] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:11] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:16] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:21] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:26] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:31] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:36] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:41] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:46] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:51] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:27:56] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:01] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:07] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:12] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:17] "GET /health HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:10] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:15] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:20] "GET /health HTTP/1.1" 200 -
backend-2  | W bazie jest 89 hashy
backend-2  |  * Serving Flask app 'app'
backend-2  |  * Debug mode: off
backend-2  | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
backend-2  |  * Running on all addresses (0.0.0.0)
backend-2  |  * Running on http://127.0.0.1:5000
backend-2  |  * Running on http://172.19.0.6:5000
backend-2  | Press CTRL+C to quit
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:00] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:05] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:26] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:31] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:36] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:41] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:46] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:51] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:28:56] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:29:01] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:29:06] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:29:11] "GET /health HTTP/1.1" 200 -
backend-3  | 127.0.0.1 - - [18/Nov/2026 23:29:16] "GET /health HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | check: hash=bc454...
backend-1  | 172.19.0.4 - - [18/Nov/2026 23:28:21] "POST /check HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:22] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:27] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:32] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:37] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:42] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:47] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:52] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:28:57] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:10] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:16] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:21] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:29:02] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:29:07] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:29:13] "GET /health HTTP/1.1" 200 -
backend-1  | 127.0.0.1 - - [18/Nov/2026 23:29:18] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:26] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:31] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:36] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:41] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:46] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:51] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:28:56] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:29:01] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:29:06] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:29:11] "GET /health HTTP/1.1" 200 -
backend-2  | 127.0.0.1 - - [18/Nov/2026 23:29:16] "GET /health HTTP/1.1" 200 -








.....................................................
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose down
[+] down 4/4
 ✔ Container metody_wirt_lab-frontend-1 Removed                                                              0.4s
 ✔ Container metody_wirt_lab-backend-1  Removed                                                              3.3s
 ✔ Container metody_wirt_lab-db-1       Removed                                                              0.2s
 ✔ Network metody_wirt_lab_default      Removed                                                              0.2s





PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose up -d --build
[+] Building 1.6s (21/21) FINISHED                                                                               
 => [internal] load local bake definitions                                                                  0.0s
 => => reading from stdin 1.16kB                                                                            0.0s
 => [frontend internal] load build definition from Dockerfile                                               0.0s
 => => transferring dockerfile: 229B                                                                        0.0s
 => [backend internal] load build definition from Dockerfile                                                0.0s
 => => transferring dockerfile: 367B                                                                        0.0s
 => [frontend internal] load metadata for docker.io/library/nginx:alpine                                    0.7s
 => [backend internal] load metadata for docker.io/library/python:3.12-slim                                 0.7s
 => [frontend internal] load .dockerignore                                                                  0.0s
 => => transferring context: 68B                                                                            0.0s
 => [backend internal] load .dockerignore                                                                   0.0s
 => => transferring context: 81B                                                                            0.0s
 => [frontend 1/3] FROM docker.io/library/nginx:alpine@sha256:0563c36f94a6d3ec3584161b77859f740f7e20b4853f  0.0s
 => => resolve docker.io/library/nginx:alpine@sha256:0563c36f94a6d3ec3584161b77859f740f7e20b4853f52c796a86  0.0s
 => [frontend internal] load build context                                                                  0.0s
 => => transferring context: 120B                                                                           0.0s
 => [backend 1/5] FROM docker.io/library/python:3.12-slim@sha256:5e2bdb1b0d542d5039cffb8181c65930093949194  0.0s
 => => resolve docker.io/library/python:3.12-slim@sha256:5e2bdb1b0d542d5039cffb8181c65930093949194a65c365d  0.0s
 => [backend internal] load build context                                                                   0.0s
 => => transferring context: 63B                                                                            0.0s
 => CACHED [frontend 2/3] COPY index.html style.css script.js /usr/share/nginx/html/                        0.0s
 => CACHED [frontend 3/3] COPY nginx.conf /etc/nginx/conf.d/default.conf                                    0.0s
 => [frontend] exporting to image                                                                           0.1s
 => => exporting layers                                                                                     0.0s
 => => exporting manifest sha256:56fbbea494adade4fa2d1871ffd40fd25f47fd1be64141d4899b443fd81b4c3d           0.0s
 => => exporting config sha256:2de625971e96d298047f17b987077f82ec985cea44a7585586b48f648ecdcabb             0.0s
 => => exporting attestation manifest sha256:53a17e66a0b4c6119ec5bd9210dbfade929728dc5ae7a3be3e288a317c23d  0.0s
 => => exporting manifest list sha256:0747f80e1afb67c06ac07c1936a0109e5d1cec51b1e07c8e3fb9dc0bdeaa37a0      0.0s
 => => naming to docker.io/library/metody_wirt_lab-frontend:latest                                          0.0s
 => => unpacking to docker.io/library/metody_wirt_lab-frontend:latest                                       0.0s
 => CACHED [backend 2/5] WORKDIR /app                                                                       0.0s
 => CACHED [backend 3/5] COPY requirements.txt .                                                            0.0s
 => CACHED [backend 4/5] RUN pip install --no-cache-dir -r requirements.txt                                 0.0s
 => CACHED [backend 5/5] COPY app.py .                                                                      0.0s
 => [backend] exporting to image                                                                            0.1s
 => => exporting layers                                                                                     0.0s
 => => exporting manifest sha256:ab3ab8b07cd08f0fe2615653b8c4531a8994ccc05acfd51c42019cc4f0f1891e           0.0s
 => => exporting config sha256:ebd34281a5186113ef602131041da04658fd7dd98c08b3183b8f62b25dd5d870             0.0s
 => => exporting attestation manifest sha256:afde0afd20341b05d1839fe65f008feb134a20edb996ef15a618beab78e9a  0.0s
 => => exporting manifest list sha256:2a157b01a25c66f4da7db8817116bcd201a6a1b711d52ec6deecd79dd461a191      0.0s
 => => naming to docker.io/library/metody_wirt_lab-backend:latest                                           0.0s
 => => unpacking to docker.io/library/metody_wirt_lab-backend:latest                                        0.0s
 => [frontend] resolving provenance for metadata file                                                       0.0s
 => [backend] resolving provenance for metadata file                                                        0.0s
[+] up 6/6
 ✔ Image metody_wirt_lab-backend        Built                                                                1.7s
 ✔ Image metody_wirt_lab-frontend       Built                                                                1.7s
 ✔ Network metody_wirt_lab_default      Created                                                              0.0s
 ✔ Container metody_wirt_lab-db-1       Healthy                                                              5.9s
 ✔ Container metody_wirt_lab-backend-1  Healthy                                                             11.5s
 ✔ Container metody_wirt_lab-frontend-1 Started                                                             11.6s




PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose ps
NAME                         IMAGE                      COMMAND                  SERVICE    CREATED          STATUS                    PORTS
metody_wirt_lab-backend-1    metody_wirt_lab-backend    "python app.py"          backend    15 seconds ago   Up 8 seconds (healthy)    5000/tcp
metody_wirt_lab-db-1         postgres:16-alpine         "docker-entrypoint.s…"   db         15 seconds ago   Up 14 seconds (healthy)   5432/tcp
metody_wirt_lab-frontend-1   metody_wirt_lab-frontend   "/docker-entrypoint.…"   frontend   15 seconds ago   Up 3 seconds              0.0.0.0:8080->80/tcp, [::]:8080->80/tcp
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 



















>> C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 
INSERT 0 1                                                      curl.exe -X POST http://localhost:8080/api/check -H "Content-Type: application/json" -d "{\`"hash\`":\`"bc45408273d7e1914b741c3407b0b559764f7876\`"}"ts\wirtualiz\Metody_wirt_lab> 
{"found":true}





PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose down
[+] down 4/4
 ✔ Container metody_wirt_lab-frontend-1 Removed                                                                        0.4s
 ✔ Container metody_wirt_lab-backend-1  Removed                                                                        3.2s
 ✔ Container metody_wirt_lab-db-1       Removed                                                                        0.2s
 ✔ Network metody_wirt_lab_default      Removed                                                                        0.3s
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose up -d
[+] up 4/4
 ✔ Network metody_wirt_lab_default      Created                                                                        0.0s
 ✔ Container metody_wirt_lab-db-1       Healthy                                                                        5.9s
 ✔ Container metody_wirt_lab-backend-1  Healthy                                                                       11.5s
 ✔ Container metody_wirt_lab-frontend-1 Started                                                                       11.7s


PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> curl.exe -X POST http://localhost:8080/api/check -H "Content-Type: application/json" -d "{\`"hash\`":\`"bc45408273d7e1914b741c3407b0b559764f7876\`"}"
{"found":true}


PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose down -v
[+] down 5/5
 ✔ Container metody_wirt_lab-frontend-1 Removed                                                                        0.3s
 ✔ Container metody_wirt_lab-backend-1  Removed                                                                        3.2s
 ✔ Container metody_wirt_lab-db-1       Removed                                                                        0.2s
 ✔ Volume metody_wirt_lab_pgdata        Removed                                                                        0.0s
 ✔ Network metody_wirt_lab_default      Removed                                                                        0.3s
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker compose up -d
[+] up 5/5
 ✔ Network metody_wirt_lab_default      Created                                                                        0.0s
 ✔ Volume metody_wirt_lab_pgdata        Created                                                                        0.0s
 ✔ Container metody_wirt_lab-db-1       Healthy                                                                        5.9s
 ✔ Container metody_wirt_lab-backend-1  Healthy                                                                       11.5s
 ✔ Container metody_wirt_lab-frontend-1 Started                                                                       11.6s




PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> curl.exe -X POST http://localhost:8080/api/check -H "Content-Type: application/json" -d "{\`"hash\`":\`"bc45408273d7e1914b741c3407b0b559764f7876\`"}"
{"found":false}
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 

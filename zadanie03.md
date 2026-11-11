Zadanie 1

PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker inspect --format '{{json .Config.Labels}}' anastasiya-drako-frontend:v1
{"maintainer":"imie.nazwisko@example.com"}


PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker inspect --format '{{json .Config.Labels}}' anastasiya-drako-frontend:latest
{"maintainer":"imie.nazwisko@example.com"}


PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker history anastasiya-drako-frontend:v1
IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
2f907f3056e3   10 minutes ago   EXPOSE [80/tcp]                                 0B        buildkit.dockerfile.v0
<missing>      10 minutes ago   COPY . /usr/share/nginx/html # buildkit         32.8kB    buildkit.dockerfile.v0
<missing>      10 minutes ago   LABEL maintainer=imie.nazwisko@example.com      0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      RUN /bin/sh -c set -x     && apkArch="$(cat …   52.4MB    buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV ACME_VERSION=0.4.1                          0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV NJS_RELEASE=1                               0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV NJS_VERSION=1.0.2                           0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      CMD ["nginx" "-g" "daemon off;"]                0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      STOPSIGNAL SIGQUIT                              0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      EXPOSE map[80/tcp:{}]                           0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENTRYPOINT ["/docker-entrypoint.sh"]            0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY 30-tune-worker-processes.sh /docker-ent…   16.4kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY 20-envsubst-on-templates.sh /docker-ent…   12.3kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY 15-local-resolvers.envsh /docker-entryp…   12.3kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY 10-listen-on-ipv6-by-default.sh /docker…   12.3kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY docker-entrypoint.sh / # buildkit          8.19kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      RUN /bin/sh -c set -x     && addgroup -g 101…   5.75MB    buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV DYNPKG_RELEASE=1                            0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV PKG_RELEASE=1                               0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV NGINX_VERSION=1.31.8                        0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      LABEL maintainer=NGINX Docker Maintainers <d…   0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      CMD ["/bin/sh"]                                 0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ADD alpine-minirootfs-3.24.3-x86_64.tar.gz /…   9.08MB    buildkit.dockerfile.v0




PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker history anastasiya-drako-frontend:latest
IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
2f907f3056e3   10 minutes ago   EXPOSE [80/tcp]                                 0B        buildkit.dockerfile.v0
<missing>      10 minutes ago   COPY . /usr/share/nginx/html # buildkit         32.8kB    buildkit.dockerfile.v0
<missing>      10 minutes ago   LABEL maintainer=imie.nazwisko@example.com      0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      RUN /bin/sh -c set -x     && apkArch="$(cat …   52.4MB    buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV ACME_VERSION=0.4.1                          0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV NJS_RELEASE=1                               0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV NJS_VERSION=1.0.2                           0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      CMD ["nginx" "-g" "daemon off;"]                0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      STOPSIGNAL SIGQUIT                              0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      EXPOSE map[80/tcp:{}]                           0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENTRYPOINT ["/docker-entrypoint.sh"]            0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY 30-tune-worker-processes.sh /docker-ent…   16.4kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY 20-envsubst-on-templates.sh /docker-ent…   12.3kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY 15-local-resolvers.envsh /docker-entryp…   12.3kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY 10-listen-on-ipv6-by-default.sh /docker…   12.3kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      COPY docker-entrypoint.sh / # buildkit          8.19kB    buildkit.dockerfile.v0
<missing>      2 weeks ago      RUN /bin/sh -c set -x     && addgroup -g 101…   5.75MB    buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV DYNPKG_RELEASE=1                            0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV PKG_RELEASE=1                               0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ENV NGINX_VERSION=1.31.8                        0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      LABEL maintainer=NGINX Docker Maintainers <d…   0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      CMD ["/bin/sh"]                                 0B        buildkit.dockerfile.v0
<missing>      2 weeks ago      ADD alpine-minirootfs-3.24.3-x86_64.tar.gz /…   9.08MB    buildkit.dockerfile.v0
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> 


które warstwy pochodzą z obrazu bazowego, które z Twojego Dockerfile, dlaczego niektóre mają rozmiar 0B i dlaczego widać tylko Twoją wartość maintainer.



Zadanie 2
1 kont:
Thu Nov  5 07:58:31 UTC 2026

2 kont:
Thu Nov  5 07:58:31 UTC 2026

PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker run -d --name zadanie2-1 -p 8082:80 breach-checker-frontend:v4    
9f6967fe03e23104bbae1dd03311d6e9186ebe10cf161fb7bb76c4037f2c5e28
PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker run -d --name zadanie2-2 -p 8083:80 breach-checker-frontend:v4
f6579fdb98dd67b2875fd457737d98e78fecaeaa1bbec7236e90c6700e727349



PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker ps
CONTAINER ID   IMAGE                            COMMAND                  CREATED              STATUS              PORTS                                     NAMES
f6579fdb98dd   breach-checker-frontend:v4       "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8083->80/tcp, [::]:8083->80/tcp   zadanie2-2
9f6967fe03e2   breach-checker-frontend:v4       "/docker-entrypoint.…"   2 minutes ago        Up 2 minutes        0.0.0.0:8082->80/tcp, [::]:8082->80/tcp   zadanie2-1


 dlaczego czas w build.txt jest taki sam w obu kontenerach i nie jest to czas ich uruchomienia?

 Zadanie 3

 server 
    listen       80;
    server_name  localhost;

    #access_log  /var/log/nginx/host.access.log  main;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }


Zadanie 4

PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker run -d --name frontend -p 8084:80 zadanie5                  
592a9b0c788ec23d87ce6ca7625fa356fd764a60c9feca1cb6081b9f201bf6b1

PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker exec zadanie5 ls /usr/share/nginx
html
index.html
script.js
style.css

PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker exec zadanie5 ls /usr/share/nginx/html
50x.html
build.txt
index.html












Zadanie 5

PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker rmi breach-checker-frontend:latest
Untagged: breach-checker-frontend:latest    

czy obraz v2 nadal istnieje? Tak

IMAGE                              ID             DISK USAGE   CONTENT SIZE   EXTRA
anastasiya-drako-frontend:latest   2f907f3056e3       93.6MB         26.3MB    U   
anastasiya-drako-frontend:v1       2f907f3056e3       93.6MB         26.3MB    U   
breach-checker-frontend:v1         b57ca70976b1       93.6MB         26.3MB    U   
breach-checker-frontend:v2         3b51deab7dab       93.6MB         26.3MB    U   
breach-checker-frontend:v3         d96fef2fc7f8       93.6MB         26.3MB    U   
breach-checker-frontend:v4         4a7f8defabb7       93.7MB         26.3MB    U   


PS C:\Users\ad800\OneDrive\Documents\wirtualiz\Metody_wirt_lab> docker rmi breach-checker-frontend:v2
Untagged: breach-checker-frontend:v2
Deleted: sha256:3b51deab7dab72a1ba11f830c6872dced61941b15bdae947cd02385a676ab821


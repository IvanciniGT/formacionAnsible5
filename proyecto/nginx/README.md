Queremos un play que nos:

- Asegure que nginx está instalado (Servidor web)
- Que tiene la configuración que me interesa
- Que está sirviendo una web que tengo en un repositorio de GIT

server {
        listen 80;
        server_name localhost;
        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;
}


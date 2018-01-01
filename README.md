# README

Proyecto incial:

	 https://github.com/pepeul1191/ruby-gestion

Dependencias:

+ Servidor Lighttpd o Nginx con CORS habilidatado
+ NodeJS
+ Gulp y Bower

Instalación de Lighttpd Server

	$ sudo apt-get install lighttpd

Habilitar CORS y cambiar de puerto:

	$ sudo nano /etc/lighttpd/lighttpd.conf

```
server.modules = (
	"mod_access",
	"mod_alias",
	"mod_compress",
 	"mod_redirect",
#       "mod_rewrite",
)

server.modules += ( "mod_setenv" )

server.document-root        = "/home/pepe/Documentos/lighttpd"
server.upload-dirs          = ( "/var/cache/lighttpd/uploads" )
server.errorlog             = "/var/log/lighttpd/error.log"
server.pid-file             = "/var/run/lighttpd.pid"
server.username             = "www-data"
server.groupname            = "www-data"
server.port                 = 81

setenv.add-response-header =  ( "Access-Control-Allow-Origin" => "http://localhost:3000")

index-file.names            = ( "index.php", "index.html", "index.lighttpd.html" )
url.access-deny             = ( "~", ".inc" )
static-file.exclude-extensions = ( ".php", ".pl", ".fcgi" )

compress.cache-dir          = "/var/cache/lighttpd/compress/"
compress.filetype           = ( "application/javascript", "text/css", "text/html", "text/plain" )

# default listening port for IPv6 falls back to the IPv4 port
## Use ipv6 if available
#include_shell "/usr/share/lighttpd/use-ipv6.pl " + server.port
include_shell "/usr/share/lighttpd/create-mime.assign.pl"
include_shell "/usr/share/lighttpd/include-conf-enabled.pl"
```

	$ sudo service lighttpd restart

Instalación de dependencias

	$ bower install && npm install

Generación de archivos con Gulp:

	$ gulp layout app swp-plugins accesos maestros estaciones agricultores 

---

### Fuentes:

+ https://github.com/pepeul1191/tutoriales/blob/master/NodeJs.md
+ https://github.com/pepeul1191/tutoriales/blob/master/Servidores-Puertos.md
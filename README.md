> # :copyright: https://github.com/lucia-blanco/CRUD
> **Proyecto bifurcado**
>
> ## MYSQL
> - Usuario: root
> - Contraseña: (sin contraseña)
> - Base de datos: **planticas**
>
> ## DESPLIEGUE EN UBUNTU 
>
> ### Instalación de software
> ```console
> sudo  apt  install  git  mysql-client  mysql-server  tomcat8  tomcat8-admin 
> ``` 
> ### Descarga de código fuente
> ```console
> git  clone  https://github.com/iesvelez-daw/JSP_CRUD_huerto.git  &&  cd  JSP_CRUD_huerto
> ```
>
> ### Introducción de datos
> ```console
> sudo su  # (Introducidos nuestra contraseña, para obtener acceso como root)
> 
> # Cambiamos el plugin de autenticación de auth_socket a mysql_native_password. 
> # Es necesario para que la aplicación conecte correctamente al servidor MySQL.
> echo "ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY ''" | mysql -u root
>
> echo "drop database if exists planticas; create database planticas" | mysql -u root
> cat DB/planticas.sql | mysql -u root -D planticas
> ```
> ### Despliegue en Tomcat 8
> ```console
> sudo su  # (Introducidos nuestra contraseña, para obtener acceso como root)
> 
> cp  mysql-connector-java-5.1.21.jar  /var/lib/tomcat8/lib
> cp  -r  planticasJSP/web  /var/lib/tomcat8/webapps/huerto
> ```
> **NOTA:** Deberás reiniciar Tomcat para que los archivos de `/var/lib/tomcat8/lib` se carguen.
>
> ```bash
> sudo  systemctl  restart  tomcat8
> ```
>
> ### Ejecutar aplicación
>
> Abrimos en el navegador la URL http://localhost:8080/huerto
>
> NOTA: 
>   - Es necesario dar un usuario de alta en el enlace de Registrarse. 
>   - Luego creamos Nuevo Huerto.
>   - Luego pulsamos Ir al huerto
>   - Luego creamos Nuevo Cultivo.
>

# :seedling: CRUD HUERTO 
CRUD para organizar un huerto.
Cada usuario podrá gestionar su huerto y añadir nuevos cultivos.  

Si estás buscando la primera versión, haz click en Branch y busca el Tag v1.0, ahí está la versión anterior.

# Nuevas funcionalidades

## Nueva pestaña FaQ
![FaQ](img/faq1.PNG)

## Display de cultivos disponibles
![Display cultivos](img/faq.PNG)
A través de un HashMap de ArrayLists, muestra los cultivos disponibles clasificados por tipo.


 

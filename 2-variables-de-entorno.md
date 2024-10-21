# Variables de Entorno
### ¿Qué son las variables de entorno
# COMPLETAR

### Para crear un contenedor con variables de entorno?

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

![variables_solu_01](img_solu/variables_solu_01.png)

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR

### Crear un contenedor con mysql:8 , mapear todos los puertos
![variables_solu_02](img_solu/variables_solu_02.png)

### ¿El contenedor se está ejecutando?
No.
***

### Identificar el problema
Falta las variables de entorno, al menos una de las siguientes debe ser especificada.
- MYSQL_ROOT_PASSWORD
- MYSQL_ALLOW_EMPTY_PASSWORD
- MYSQL_RANDOM_ROOT_PASSWORD
![variables_solu_03](img_solu/variables_solu_03.png)


### Eliminar el contenedor creado con mysql:8 
![variables_solu_04](img_solu/variables_solu_04.png)

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo
```
Set-Content -Path "C:\Users\Kevin Pc\en_Var_Dck\.env" -Value "MYSQL_ROOT_PASSWORD=admin`nMYSQL_DATABASE=MyBD`nMYSQL_USER=admin`nMYSQL_PASSWORD=gr2sw
```
![variables_solu_05](img_solu/variables_solu_05.png)

```
docker run P -d --name mysql-cont --env-file="C:\Users\Kevin Pc\en_Var_Dck\.env" mysql:8
```
![variables_solu_06](img_solu/variables_solu_06.png)

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR 
![variables_solu_06](img_solu/variables_solu_06.png)

## ¿Qué bases de datos existen en el contenedor creado?
![variables_solu_07](img_solu/variables_solu_07.png)
![variables_solu_08](img_solu/variables_solu_08.png)
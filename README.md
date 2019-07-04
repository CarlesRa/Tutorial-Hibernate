# Tutorial Java Maven Hibernate
## Todos los fragmentos para copiar en POM.xml los podemos encontrar en [mvnrepository](https://mvnrepository.com/)
## Pasos a seguir
### 1º-Creamos un proyecto Maven en nuestro ide favorito.
### 2º-Creamos la etiqueta build en el arxivo POM.xml y copiamos el código.
    Este fragmento de código sirve para pedirle a maven que use java 8 porque es compatible con Hibernate.
```xml
<build>

    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.8.1</version>
            <configuration>
                <source>1.8</source>
                <target>1.8</target>
            </configuration>
        </plugin>
    </plugins>

</build>
```
### 3º-Creamos la etiqueta dependences en POM.xml donde copiaremos los códigos para instalar las dependencias.
  3.1 instalamos hibernate-core
```xml
  <dependency>
      <groupId>org.hibernate</groupId>
      <artifactId>hibernate-core</artifactId>
      <version>5.4.1.Final</version>
  </dependency>
```
  3.2 instalamos javax:persistence para tener soporte con la api JPA(java persistence api)
```xml
  <dependency>
      <groupId>javax.persistence</groupId>
      <artifactId>persistence-api</artifactId>
      <version>1.0.2</version>
  </dependency>
```
   3.3 instalamos hibernate-entitymanager que funcionara de interconecsión entre JPA y hibernate(SOLO SI DA PROBLEMAS) 
```xml
  <dependency>
      <groupId>org.hibernate</groupId>
      <artifactId>hibernate-entitymanager</artifactId>
      <version>5.4.3.Final</version>
  </dependency> 
```
  3.4 importamos la base de datos que queremos utilizar, en este caso el driver JDBC(java database connect) para MySQL
```xml
  <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>8.0.16</version>
  </dependency>
```
### 4º Creamos el archivo de configuración de hibernate.
   Hay que crear una carpeta en el directorio src/main/resources con el nombre "META-INF" y crear un archivo "persistence.xml" dentro de la carpeta "META_INF" con el siguiente código:
```xml
<?xml version="1.0" encoding="UTF-8" ?>
  <!-- La etiqueta <persistence> sirve para indicar que es un archivo de persistencia -->
    <persistence xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://java.sun.com/xml/ns/persistence
        http://java.sun.com/xml/ns/persistence/persistence_2_0.xsd"
        version="2.0" xmlns="http://java.sun.com/xml/ns/persistence">
<!-- En la etiqueta <persistence-unit> es donde van a estar todos los parametros de conexión (Se necesita una como mínimo)
el "name =" puede ser el que queramos, sirve para poder llamarlo despues-->
<persistence-unit name="persistencia">
    <!--Con la etiqueta <class> identificamos las clases que queremos que el gestor de persistencia trate,
estas clases son las que tendran las anotaciones JPA-->
    <class>com.carlesramos.hibernate.modelo.Empleado</class>
    <properties>
        <!--Driver de la base de datos que queramos utilizar-->
        <property name="javax.persistence.jdbc.driver" value="com.mysql.jdbc.Driver" />
        <!--Url de la conexión con la database-->
        <property name="javax.persistence.jdbc.url" value="jdbc:mysql://localhost:3306/elecciones"/>
        <!--Nombre de usuario-->
        <property name="javax.persistence.jdbc.user" value="root" />
        <!--Password-->
        <property name="javax.persistence.jdbc.password" value="" />
        <!--El dialect sirve para que hibernate se "entienda" con la database y poder realizar operaciones en ella-->
        <property name="hibernate.dialect" value="org.hibernate.dialect.MySQL8Dialect" />
        <!--Con esta propiedad le decimos el comportamiento general con la base de datos, en el caso de poner "create", hibernate creara la base de datos en caso de que no exista o la actualizara, tambien tenemos "validate", "update", "create-drop"-->
        <property name="hibernate.hbm2ddl.auto" value="create" />
    </properties>
 </persistence-unit>

</persistence>
```
## Con los pasos previos ya quedaria configurada la conexión con la base de datos.


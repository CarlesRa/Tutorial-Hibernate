# Tutorial Java Maven Hibernate
## Todos los fragmentos para copiar en POM.xml los podemos encontrar en [](https://mvnrepository.com/)
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
  3.4 importamos la base de datos que queremos utilizar, en este caso MySQL
```xml
  <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>8.0.16</version>
  </dependency>
```


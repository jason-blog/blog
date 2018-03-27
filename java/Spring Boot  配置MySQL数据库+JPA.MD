<pre class="prettyprint lang-js linenums">http://blog.csdn.net/cool__wang/article/details/49495165
</pre>
<pre class="prettyprint lang-js linenums">
</pre>
<pre class="prettyprint lang-js linenums">#DB Configuration:
spring.datasource.driverClassName = com.mysql.jdbc.Driver
spring.datasource.url = jdbc:mysql://localhost:3306/testdb
spring.datasource.username = root
spring.datasource.password = 123456

#JPA Configuration:  
spring.jpa.database=MySQL
spring.jpa.show-sql=true  
spring.jpa.generate-ddl=true  
spring.jpa.hibernate.ddl-auto=update  
#spring.jpa.database-platform=org.hibernate.dialect.MySQL5Dialect  
spring.jpa.hibernate.naming_strategy=org.hibernate.cfg.ImprovedNamingStrategy  
#spring.jpa.database=org.hibernate.dialect.MySQL5InnoDBDialect 
#spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MYSQL5Dialect</pre>